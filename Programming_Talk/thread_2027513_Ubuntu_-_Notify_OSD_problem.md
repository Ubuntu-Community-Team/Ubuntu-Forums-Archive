---
title: "Ubuntu - Notify OSD problem"
date: 2012-07-16
forum: Programming Talk
---

### Post by chevloschelios on 2012-07-16
Hi,

I am writing simple python script that shows notifications via NotifyOSD. The script require 'root' privileges to run.  So my code looks like this -- ```
 su MY_USERNAME -c notify-send ......... 
``` - i must switch user because I´m not logged as root so it does not appear to me. The problem is, when I run GUI for this with  ```
 gksu python scriptGUI.py 
``` it does not work. 

Any advices ?? Thank you . [sorry for my bad english]

---

