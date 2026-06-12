---
title: "How to use php-gd  create a graph from data that is stored inside a sqlite database?"
date: 2013-03-18
forum: Programming Talk
---

### Post by Newbie89 on 2013-03-18
I can't find any on the website...any simple tutorial for this kind of problem?

---

### Post by tgalati4 on 2013-03-18
Try searching for php5-gd in google.

[http://php.net/manual/en/book.image.php](http://php.net/manual/en/book.image.php)

Typically you would do an SQL query on the data that you are interested in and dump it to a file, then use php5-gd to read that file and plot your data.

I don't know of a way to directly plot SQL query data from php5-gd without an intermediate step.

Normally when you can't find how to do something, you might be using the wrong tool.  For instance:  "How do I draw an SQL graph using an eggbeater?"  You won't get many hits.  But, "How do I draw a graph with PHP" brings up a lot of hits:

[http://pchart.sourceforge.net/](http://pchart.sourceforge.net/)
[https://developers.google.com/chart/image/docs/gallery/chart_gall](https://developers.google.com/chart/image/docs/gallery/chart_gall)
[http://teethgrinder.co.uk/open-flash-chart-2/](http://teethgrinder.co.uk/open-flash-chart-2/)
[http://graphpite.sourceforge.net/](http://graphpite.sourceforge.net/)
[http://www.jscharts.com/](http://www.jscharts.com/)
[http://stackoverflow.com/questions/10876917/need-suggestions-to-draw-a-graph-in-php-from-mysql](http://stackoverflow.com/questions/10876917/need-suggestions-to-draw-a-graph-in-php-from-mysql)

php5-gd may be an eggbeater for this application.  Not the right tool for the job.

---

