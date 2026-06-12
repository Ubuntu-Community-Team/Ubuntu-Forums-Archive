---
title: "System program problem detected"
date: 2019-08-14
forum: New to Ubuntu
---

### Post by jim Kane on 2019-08-14
Recently installed Xubuntu 18.4 and now have this error message on statup but no clue as to what is wrong 
“System program problem detected” 
have run software update but error persists 
everything seems to be working ok 
How do I find out what the problem is 
Thanks


Thanks[IMG]https://i.vgy.me/HLRsRL.png[/IMG]

---

### Post by cruzer001 on 2019-08-14
Looks like Apport
[https://wiki.ubuntu.com/Apport](https://wiki.ubuntu.com/Apport)
Chances are you just need to reset apport.
```
sudo rm /var/crash/*
```
The report will regenerate if the problem persist.

---

### Post by guiverc on 2019-08-14
The message means some program crashed.  If you look in /var/crash/ you'll see crash reports that you can peruse to get details of what program crashed (and what you'll upload if you report the problem). 

The file name tells gives you a quick clue as to the program/library where the issue was caught, and the date/time when the crash occurred (though details are inside file as well). 

The files are ASCII text, so you can peruse them without worry (the binary parts are converted to text). If you reported the problem a .upload file will be seen so it doesn't get reported again (`ubuntu-bug` is the program that allows you to submit at a later stage).  

For further information, this may help [https://help.ubuntu.com/community/ReportingBugs](https://help.ubuntu.com/community/ReportingBugs)

---

### Post by jim Kane on 2019-08-15
Thank for your help
 it was (surprise:) Windows on a VM that had crashed 
all sorted now

---

