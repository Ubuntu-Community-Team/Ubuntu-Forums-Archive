---
title: "SQL - What can I use?"
date: 2010-11-02
forum: Programming Talk
---

### Post by fallenshadow on 2010-11-02
I was going to install Ingres tonight on my PC but after reading that Visual DBA is not included in the Linux edition I don't really want to install it anymore.

So firstly, is there some community GUI for Ingres which I can use instead?

If not, is there any alternative for testing my SQL code and having a graphical UI for looking at it/modifying it?

---

### Post by juancarlospaco on 2010-11-02
SQLite ?

---

### Post by NertSkull on 2010-11-02
I'm not sure I know exactly what you mean by that.  But you could install open office base with the connection driver and use it to look at the SQL code in a graphical way.  

There's also mysql administrator (in the repos I believe, at least used to be).

PHPMyAdmin is also available.  

Maybe some of those are what you are looking for?

---

### Post by Some Penguin on 2010-11-02
[http://www.razorsql.com/features/ingres_visual_tools.html](http://www.razorsql.com/features/ingres_visual_tools.html)
?

---

### Post by fallenshadow on 2010-11-03
I already investigated Razorsql... its a trial version of a paid product so thats not very good.

I was under pressure last night to check if my code works, so I had to install Ingres Database in a Windows virtual machine. :P

In future I would prefer to be able to test my code on Ubuntu, so I might try MySQL Administrator.

I also found this which looks like a more up to date alternative to MySQL Administrator:

[http://dev.mysql.com/downloads/workbench/](http://dev.mysql.com/downloads/workbench/)

Workbench even has .deb installers for Ubuntu... pretty sweet! :)

---

### Post by spjackson on 2010-11-03
> **fallenshadow said:**
> 
I was under pressure last night to check if my code works, so I had to install Ingres Database in a Windows virtual machine. :P

I don't follow why you need Visual DBA to test your code. I have written and tested Ingres applications on Linux, but that was several years ago.

---

### Post by fallenshadow on 2010-11-04
I am not testing applications but just testing SQL code and I want to be able to easily see/check the results.

---

### Post by spjackson on 2010-11-04
> **fallenshadow said:**
> I am not testing applications but just testing SQL code and I want to be able to easily see/check the results.
I still don't see why you need Visual DBA in order to check what SQL code has done. But if you've convinced yourself that you do and you are happy to use Windows, then so be it.

---

### Post by fallenshadow on 2010-11-04
Actually my end goal is to use workbench GUI on Linux but I haven't had the time to install and test it yet.

---

