---
title: "cups is a real PROBLEM!"
date: 2013-12-24
forum: New to Ubuntu
---

### Post by schmitta on 2013-12-24
I go to print a page. Unfortunately CUPS is installed. I starts out with nothing printing and the job PENDING. I click on ENABLE, the job prints out about 5 pages and stops. I look at the job and its PENDING again. I click on ENABLE and the JOB STARTS OVER WITH THE FIRST PAGE! THEN PRINTS 5 PAGES AND STOPS WITH THE JOB PENDING!  This continues forever. I double click on the printer and get Stopped - /usr/lib/cups/backend/hp failed for the printer state. I really do not know what is going on. I would like to dump CUPS and just print from UBUNTU but I don't know how. All I am trying to do is print out a VIM user guide so I can learn VIM. I like UBUNTU and do not have this problem with other machines

---

### Post by Gone fishing on 2013-12-24
Try using the CUPS admin system open a browser and go to localhost:631 hopefully under manage printers you will get more information about the problem. I would probably remove the printer and the reinstall from the cups admin system in my experience usually hp printers work try a different driver?

---

### Post by tgalati4 on 2013-12-24
Look in /var/log/cups for log files.  There are usually descriptive messages as to what is going on.  CUPS is the printing framework for linux, so mastery of it is part of the delight of using linux.  Oh, and you can print across the internet with it.  Spend some time here:  [http://cups.org/documentation.php](http://cups.org/documentation.php)

---

