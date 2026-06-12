---
title: "MySQL Search"
date: 2007-11-08
forum: Programming Talk
---

### Post by 71fnRVVm on 2007-11-08
Hey everyone,

I'm trying to develop a good search method for a PHP-based "web application", and I'm having problems.  I realize that other options might be easier and more efficient, but there's a few extenuating circumstances...

Full details are here:  [http://www.kyle-brady.com/2007/11/07/mysql-search/](http://www.kyle-brady.com/2007/11/07/mysql-search/)

Any help is appreciated.

Thanks

---

### Post by smartbei on 2007-11-08
What some people do in this case is append all the relevant fields (the fields you want to be searchable) into a text record in the database and just search that field. I have not done this myself, so I am not sure how fast/slow it is but I know that there are sites that do this (have worked on them, but not in a major decision-making position).


EDIT: After looking up the site below, I believe that it is the far better way to do this (rather than the way I described above)
See [http://dev.mysql.com/doc/refman/5.0/en/fulltext-search.html](http://dev.mysql.com/doc/refman/5.0/en/fulltext-search.html) for more information.

---

### Post by 71fnRVVm on 2007-11-08
I thought of that, and tried it before using what I do now, and it's really slow.  Very slow.

Not to mention the code is really ugly to make that work.  I was hoping someone had ideas on a "MySQL Search Algorithm", like a Holy Grail of sorts...

---

### Post by smartbei on 2007-11-08
Which are you talking about? Appending all the data to a single field or using the FULLTEXT index?

Could you give me a bit more information about the type of data you want to search, the amount of data to be searched, etc?

---

### Post by 71fnRVVm on 2007-11-08
Sure.

The tables are strucutred a little differently depending on which is being accessed, but it's all very similar...all content is separated into different fields:  title, body, user, date, time, etc.

I had previously tried condensing all of a row's data into one entry, although inside a text file... this was slow.

How would I use FULLTEXT for this?  That sounds like a good idea, potentially, but I'm a little blurry on what that would do/how it would work...

Thanks

---

