![首页 -c600](home.jpg)
![后台 -c600](back.png)
## 每日仅允许投一票
每次投票便记入投票表中，

代码采用实现方式一：
判断 vote 表（用户投票表） 中存在用户的投票数据则无法再次进行投票，
使用 crontab 定时任务每晚12:00清空投票表。
在 posts表（作品表） 设置投票数字段，投票时执行 +1.

每日允许多次投票扩展：
判断表中字段出现的次数即可。

## 防止刷票
添加阅读次数，
当“投票数/每日可投票数量 > 阅读数”则有刷票行为。
那么每日对投票表进行清空就不是很科学了，
无法检测每个作品的投票情况。

实现方式二：
不用设置定时任务，
对用户今日的投票进行检测，
虽然之后也可以对作品的投票数据进行 count 从而检测投票总数，
不过保留 posts 表中的 count 在数据量大的情况更有优势。

