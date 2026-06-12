---
title: "[SOLVED] C++ Library Question"
date: 2008-03-13
forum: Programming Talk
---

### Post by 71fnRVVm on 2008-03-13
Hi everyone,

I'm in the process of planning how I'm going to write a program that will interact with Internet XML feeds and a MySQL database, a first time for both for me in C++.

What libraries are commonly used for MySQL handling?

Are there any good feed parsing libraries for C++?  I recently found, and really like, the Zend Feed portion of the Zend PHP Framework... I'm assuming there has to be something similar.  I'm talking about taking an XML document an automatically objectifying it, so you can reach nodes by purely calling them as an object structure.

Thanks in advance for any advice.

--Kyle

---

### Post by dempl_dempl on 2008-03-13
Check out   Sql Lite : 
  [http://www.sqlite.org/](http://www.sqlite.org/)

Heh .. I don't want to advertise myself , but you'll find couple of libraries on my site.

For Database-related frameworks/libs:

[http://www.stosha.net/component/option,com_mtree/task,listcats/cat_id,114/Itemid,/]("http://www.stosha.net/component/option,com_mtree/task,listcats/cat_id,114/Itemid,/")


For XML Libraries: 

[http://www.stosha.net/component/option,com_mtree/task,listcats/cat_id,99/Itemid,/]("http://www.stosha.net/component/option,com_mtree/task,listcats/cat_id,99/Itemid,/")



This might be also an interest for you:

Web Services.  I recommend  using WsO2 library , and avoiding Axis framework : 

[http://www.stosha.net/component/option,com_mtree/task,listcats/cat_id,161/Itemid,/]("http://www.stosha.net/component/option,com_mtree/task,listcats/cat_id,161/Itemid,/")

Cheers!

---

### Post by 71fnRVVm on 2008-03-13
Thanks for the links, but two problems:

a)  I have to *interface* with a pre-existing MySQL database structure on the server this program will be running on.
b)  I'd rather use the "normal" or "common" libraries (at least for the moment) than someone else's homegrown ones.  If for no other reason than I don't want to have to mess with the server config more than I have to.

So, after those items, any suggestions?

Thanks

---

### Post by dwhitney67 on 2008-03-13
Consider using [MySQL++]("http://tangentsoft.net/mysql++/").

---

### Post by 71fnRVVm on 2008-03-14
Thanks.  I decided to go with XML++ and MySQL++

---

### Post by dwhitney67 on 2008-03-15
I am not familiar with XML++.  My first instinct would have been to rely on the Boost libraries to interpret XML.

Anyhow, I learn't long ago that there are many ways to climb a "mountain".

Good luck with your endevour.

---

