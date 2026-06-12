---
title: "How to start Galssfish when machine start"
date: 2010-09-30
forum: Programming Talk
---

### Post by mthalis on 2010-09-30
I'm using Glassfish v2.1 server in windows xp machine. **I want to run Glassfish server when machine start**. Without out putting my bat script into widows start up(C:\Documents and Settings\ABC\Start Menu\Programs\Startup). Below show my .bat script. 

run.bat
-----------------
cd C:\Glassfish\bin
asadmin start-domain domain1
pause
---------------

Thank You

---

### Post by r-senior on 2010-09-30
There's a launchpad issue that covers this and has an example startup script:

[https://bugs.launchpad.net/ubuntu/+source/glassfish/+bug/150960]("https://bugs.launchpad.net/ubuntu/+source/glassfish/+bug/150960")

Also blogs that cover the creation of a startup script:

[http://blogs.sun.com/kkranz/entry/setting_up_glassfish_on_ubuntu]("http://blogs.sun.com/kkranz/entry/setting_up_glassfish_on_ubuntu")

[http://computingwithjasper.blogspot.com/2008/01/installing-glassfish-2-on-ubuntu-710.html]("http://computingwithjasper.blogspot.com/2008/01/installing-glassfish-2-on-ubuntu-710.html")

---

### Post by mthalis on 2010-09-30
Thanks for reply, **I want to do it windows xp machine**

---

### Post by PaulM1985 on 2010-09-30
You may get more luck if you posted this message on a Windows based forum.

---

