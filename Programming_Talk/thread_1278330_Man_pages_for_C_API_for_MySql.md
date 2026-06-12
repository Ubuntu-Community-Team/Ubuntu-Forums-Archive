---
title: "Man pages for C API for MySql"
date: 2009-09-29
forum: Programming Talk
---

### Post by dheerajsuthar on 2009-09-29
Hi,
I am on Ubuntu 9.04 tweaking some programs demanding MySql queries. I got the program working by installing following package:
  sudo apt-get install libmysqlclient-dev
and using proper include and library folder 

However I was unable to access any man pages for these C api's (Strangely for ncurses too I had to install dev packages which also beautifully added to my man pages all c function required.). Checked on the net but found only some html docs. What I really require is proper man pages for all these functions. Please do share any way possible to access them. Thanks in advance.:)

---

### Post by chrisjsmith on 2009-09-29
I doubt you can get them.  MySQL are usually terrible in the documentation department relying purely on the pitiful, purely HTML docs on [http://dev.mysql.com/doc/refman/5.1/en/dynindex-cfunction.html](http://dev.mysql.com/doc/refman/5.1/en/dynindex-cfunction.html)

---

### Post by dheerajsuthar on 2009-09-29
> **chrisjsmith said:**
> I doubt you can get them.  MySQL are usually terrible in the documentation department relying purely on the pitiful, purely HTML docs on [http://dev.mysql.com/doc/refman/5.1/en/dynindex-cfunction.html](http://dev.mysql.com/doc/refman/5.1/en/dynindex-cfunction.html)
thanks for reply buddy:)... was afraid that this may be the answer. However will utilize link provided by you and try to get the pages through wget.
However just a thought of extension. Can all those documentation in KDevelop be locally stored so as to access them even without internet. Will wait for any bright idea in this regard.:popcorn:

---

### Post by chrisjsmith on 2009-09-29
I think you can get the sources from their SVN repository.  Not 100% sure though.  If not you can probably "wget --recursive" on them :)

---

