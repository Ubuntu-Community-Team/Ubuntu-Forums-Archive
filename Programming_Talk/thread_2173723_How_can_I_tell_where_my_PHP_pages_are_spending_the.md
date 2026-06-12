---
title: "How can I tell where my PHP pages are spending the most time in functions?"
date: 2013-09-11
forum: Programming Talk
---

### Post by Maheriano on 2013-09-11
I wrote a PHP application and it's completely function based with separate classes. It takes quite a while to load some of the heavier pages so I was wondering if there's any way to see a graph of which functions is taking up most of the time. Both in the PHP and the Javascript.

---

### Post by SeijiSensei on 2013-09-11
Not that I know of, though you could sprinkle in a few commands to echo a timestamp at various points along the way.

Does this application extract information from a database?  In my experience PHP scripts themselves are never slow, but queries against a poorly-indexed SQL database can bog things down a lot.  Make sure any SELECTs use keys that have corresponding indexes in the DB; if you are selecting on multiple fields, you need an index that incorporates all those fields.  Use the SQL "analyze" command as well.

---

### Post by tgalati4 on 2013-09-11
There are several linux performance tools.  *strace* is one of them.  I don't know of any for PHP specifically, but there are some webpage metrics.  I know that sugarcrm is based on PHP and had built-in query timing so you could see which query pages were taking a long time.  I would look at the source code/PHP to see how those metrics are generated and apply to your code.

Search here:  [http://forums.sugarcrm.com/](http://forums.sugarcrm.com/)

Overview of PHP performance tweaks:  [http://support.sugarcrm.com/04_Find_Answers/02KB/02Administration/100Troubleshooting/Common_Performance_Tweaks](http://support.sugarcrm.com/04_Find_Answers/02KB/02Administration/100Troubleshooting/Common_Performance_Tweaks)

---

