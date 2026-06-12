---
title: "Ringtail (13.04) Confusing Me - Plz help"
date: 2013-07-19
forum: New to Ubuntu
---

### Post by chrisdebo on 2013-07-19
I just built a new box for Ubuntu and downloaded version 13.04. I downloaded a few programs and ran out of disk space on my new 64GB SDD.

Could someone please answer the following questions:
Is the only partition viewer/tool located in the Disks app?
When I view the Disk Usage Analyzer (DUA), it shows root as 100% full. Is this normal?
There is a message at the top of DUA that states "Can not scan folder "/" or some of the folders under it; Permission denied." I want to be able to be root (bash) before I go into Unity as to avoid this problem. How do I do that? 
I read online about how I could adjust a setting in the download manager so it will remove all archived files associated with the download. How do I do this is 13.04?
And finally, is there a way to configure what action takes place when I press the power button (shutdown, sleep, etc.)?

I know my way around a UNIX box, but Raring Ringtail is not the same.
Thanks in advance,

Chris

---

### Post by dannyboy79 on 2013-07-19
1. i am not familar with raring so I am not sure what all disk utilitites there are for it. what is your goal, to see all the partitions? have you checked out gparted BUT make sure you don't make any changes within gparted unless you want to possibly lose data
2. / being full is NOT normal and most likely you won't be able to use your computer as some space is always required to write temp files to /tmp/
3. you don't want to be running in unity as root, that's just not how ubuntu works. if you need "root" privalages temporarily than use sudo for text commands and gksudo for gui applications.
4. not sure what you're referring to for the download manager.


as to why / is 100% FULL, i am guessing you have some large log files, it's been a reoccuring issue i''ve seen with 13.04 lately. check /var/log for kern.log and syslog, they may be very large. before you delete them you can run a tail on them to see what the last 10 lines are within the log files to see if you can fix the issue of why the issue is being logged to begin with.

---

### Post by Frogs Hair on 2013-07-19
The disks tool and disk usage analyzer are the two GUI disk info tools in 13.04   From the command line/terminal you can use the following .```
 df -h
```

---

