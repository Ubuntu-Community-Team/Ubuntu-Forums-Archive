---
title: "system error"
date: 2014-12-05
forum: New to Ubuntu
---

### Post by gajanan2 on 2014-12-05
hey i m new to ubuntu 14.4,it is fantastic.but i hav a system error, the error messegewas:"unknown error:'<class'system error'>'(e:type'cdrom:(ubuntu#debtu14.04LTS_Trusty tahr_-Release i 386(20140722.2)3)/'is not know on line 1 in sourselist/etc/apt/source.list. what to do further.:mad::mad:

---

### Post by sammiev on 2014-12-05
Edit your source.list and uncheck cdrom.

---

### Post by Gone fishing on 2014-12-05
Open the dash and type software, then open "Software and Update," on the other software tab unselect the CDROM. If you want the command line open a terminal type in the following command 

```
sudo gedit /etc/apt/sources.list
```

and put a # in front of the first line

---

### Post by buzzingrobot on 2014-12-06
The "source.list" file is a list of the URL's of the servers that host the packages that can be installed via the Software Center or another similar tool.  These servers are also examined by your system to determine which updates need to be applied.

The "cdrom" entry means the CD/DVD, or USB stick, used to do the initial installation. Normally, it's disabled, but, for whatever reason, it hasn't been here.  So, your system is trying to find it every time it tries to install a package or do an update, and complains when it's not there.

---

### Post by ibjsb4 on 2014-12-06
Or use the software sources GUI and just uncheck it.

[https://help.ubuntu.com/community/Repositories/Ubuntu#CD-ROM.2BAC8-DVD](https://help.ubuntu.com/community/Repositories/Ubuntu#CD-ROM.2BAC8-DVD)

---

