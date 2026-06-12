---
title: "Learning Mysql"
date: 2006-11-18
forum: Programming Talk
---

### Post by rvickers on 2006-11-18
I need to learn mysql and was wondering what packages I need to download?:D 
Thanks

---

### Post by ciscosurfer on 2006-11-18
[This page will be of service to you]("https://help.ubuntu.com/community/ApacheMySQLPHP")!

Cheers!

---

### Post by rvickers on 2006-11-19
Yes, the page was very informative however I don't want to turn my laptop into a server nor do I have access to a server. I need a "light weight" edition of msql to learn the syntax on.
Any ideas:D
Thanks...
**************************** update *****************************
I found the pkg php5-sqlite which I downloaded and installed. However, I can't seem to figure out how to use it. Is there something else I should have downloaded and installed to be able to use mysqlite?
Thanks

---

### Post by rimian on 2006-11-20
some ISPs run a MySQL server. You might find that your provider has one and a phpmyadmin manager with it. They don't usually publicise that service much. just a thought.

---

### Post by mssever on 2006-11-20
My recommendation would be to install phpMyAdmin ```
sudo aptitude install phpmyadmin
```
This will bring in MySQL, php, and apache as dependencies. This isnt as much overhead as it seems, imo. Then, play with phpmyadmin.

I actually got started by using the mysql command line and the mysql manual, but my life would have been easier had I known about phpmyadmin.

---

### Post by rvickers on 2006-11-20
Do you know if there's a c++ interface with phpmyadmin? Right now I have sqlite interfacing with c++ and that's giving me a platform to play with sql but mysql is also something I need to be familiar with, job wise...:D 
Thanks for the replies...

---

### Post by Paul41 on 2006-11-20
There is a "MySQL Administrator" and "MySQL Query Browser" that I assume are written in C++. I can't remember the package names right now. I am at another computer right now, otherwise I would look up the names for them.

---

### Post by rvickers on 2006-11-20
Just installed all the packages you suggested. No database available to attach to but I see a lot of mysql c++ header and library files which is what I'm looking for. :cool: 
Thanks...

---

### Post by rvickers on 2006-11-20
I'm there, just accessed mysql via c++:-D 
Thanks for the help...

---

