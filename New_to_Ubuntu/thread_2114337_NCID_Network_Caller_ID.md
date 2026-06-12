---
title: "NCID Network Caller ID"
date: 2013-02-09
forum: New to Ubuntu
---

### Post by xren69 on 2013-02-09
Hi, I have installed NCID but I cannot get past the error of cannot read "sock 6" connection refused, I have server and client on same machine and am running from a USB modem on /dev/ttyACM0, can anyone help me get this working?
I am running this on a laptop running Ubuntu 12.04 lots and on an O2 joggler running xbuntu 12.10 and both have same error so I think I am missing something in the set up so any pointers would be appreciated.
Thanks

---

### Post by NickD-NLUG on 2014-02-08
Did you ever get this fixed?

---

### Post by xren69 on 2014-02-09
Hi, 

Yes it did get sorted, it was a simple setting in the NCIDD.conf file that needed a # removed, but it was very tempremental and worked sometimes but not every time. I gave up on the project and have moved on to running NCID on the raspberry pi.

What errors are you getting and what hardware have you got this set up on?

---

### Post by NickD-NLUG on 2014-02-12
Glad you got it working, and especially on a Pi.

Meanwhile, my problem is here: [http://ubuntuforums.org/showthread.php?t=2204439](http://ubuntuforums.org/showthread.php?t=2204439) - basically I'm getting weird replies from my modem, which might explain why the blacklist functionality isn't working.

---

