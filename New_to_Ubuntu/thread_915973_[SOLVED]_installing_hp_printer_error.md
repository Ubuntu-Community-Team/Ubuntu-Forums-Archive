---
title: "[SOLVED] installing hp printer error"
date: 2008-09-10
forum: New to Ubuntu
---

### Post by idasue32 on 2008-09-10
OK, I am installing an HP printer and it advises on the website when downloading the HPLIP not to install as root.  I have no idea what that means and I got this error:

error:  You are running the installer as root.  It is highly recommended that you run the installer as
error: a regular (non-root) user.  Do you still wish to continue?
Continue with installation (y=yes, n=no*, q=quit) ? n

How do I NOT run it as a root?  I am brand new to Ubuntu, so absolute beginner talk please :)

Thanks!
Cate

---

### Post by Seisen on 2008-09-10
Most HP Printers are supported out of the box in Ubuntu did you try installing the printer without installing the hplip drivers?

---

### Post by idasue32 on 2008-09-10
Yes, it is an Officejet J4580, not supported out of the box... :(  Of course I have to pick the one thats not!

Any suggestions?

---

### Post by oldos2er on 2008-09-10
Why not install hplip from the repositories?

---

### Post by bigfootnmd on 2008-09-10
There is some hope.

Go to

[http://hplip.sourceforge.net/](http://hplip.sourceforge.net/)

Click on Supported printers and you will find your printer listed.

Next click download and choose the Ubuntu 8.04 self installer and follow the instructions
on the download page.

Best of luck.

---

### Post by idasue32 on 2008-09-10
Thats what I did/was doing when the error came up...  Thats where it says not to install it as a root.  I just need to know how to not install it as a root...

---

### Post by amazingtaters on 2008-09-10
go to 

System>>Administration>>Synaptic Package Manager 

and search hplip. You can install the hplip drivers from there, no issues.

---

### Post by SunnyRabbiera on 2008-09-10
well did you enable a root account?
not really advised hope you know.

---

### Post by idasue32 on 2008-09-10
I have no clue??  Thats kinda the point of the question...?

---

### Post by idasue32 on 2008-09-10
ok nevermind i figured it out

---

### Post by justin6 on 2008-09-12
Can you specify how did you solve your [HP printer]("http://www.hpprinter.org/") related problem  as im planning to install ubuntu also with HP printer and I want to avoid this problem.

---

