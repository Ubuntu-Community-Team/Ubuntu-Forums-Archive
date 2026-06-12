---
title: "[SOLVED] Microtek 4800 scanner problem"
date: 2008-05-06
forum: New to Ubuntu
---

### Post by alienexplorers on 2008-05-06
I am trying to setup and run my Microtek 4800 scanner.  It worked correctly under Gutsy, but under Hardy I get the following error message:
[[IMG]http://img369.imageshack.us/img369/5281/screenshoterrormv0.th.png[/IMG]](http://img369.imageshack.us/my.php?image=screenshoterrormv0.png)

How would I go about fixing this problem?

Tried running the command lsusb in terminal and got this output:
> terminator@terminator-desktop:~$ lsusb
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 004: ID 05da:30cf Microtek International, Inc. ScanMaker 4800
Bus 001 Device 001: ID 0000:0000

---

### Post by alienexplorers on 2008-05-06
Checked on the SANE web page and the Microtek 4800 is reported as being good to go.  It uses the 3840 driver.  I do have libsane-extras installed along with sane and xsane.

---

### Post by alienexplorers on 2008-05-06
Bump

---

### Post by alienexplorers on 2008-05-06
Been reading around and found that the scanner user has to be listed and enabled in the scanner group.  I tried enabling myself and root in the scanner group and still have the same error reported in post 1.

---

### Post by alienexplorers on 2008-05-06
bump

---

### Post by alienexplorers on 2008-05-07
bump

---

### Post by alienexplorers on 2008-05-17
Found out that the 4800 driver from Sane is bad.  Reverting to the 1.0.15 driver fixed the problem.

---

