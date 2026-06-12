---
title: "raid driver installation"
date: 2008-11-16
forum: New to Ubuntu
---

### Post by 007casper on 2008-11-16
which redhat driver is compatible with ubuntu?...

I am building a new server... mother board asus DSEB-D16 during the raid driver installation only option I get is for win, red hat, sles...  I dont know what SLES stands for... but I am trying to figure out the best option for the driver to work with latest ubuntu...

INTEL 6321 MATRIX STORAGE MANAGER
win 32 bit (supports AHCI)
win 64 bit (supports AHCI)
-
INTEL 6321 LSI MegaRAID Driver
Win 2000 server
win 2003 32 bit
win 2003 64 bit
RHEL3 UP8 32/64 bit
RHEL4 UP5 32/64 bit
RHEL 5 32/64 bit
SLES 9.0 SP3 32 bit
SLES 9.0 SP3 64 bit
SLES 10 SP1 32 bit
SLES 10 SP1 64 bit 
-
LSI 1068 B1 SAS Driver
Win 2000 server
win 2003 32 bit
win 2003 64 bit
RHEL AS3 UP8 32 bit
RHEL AS3 UP8 64 bit
RHEL AS4 UP5 32 bit
RHEL AS4 UP5 64 bit
RHEL 5 32 bit
RHEL 5 64 bit
SLES 9.0 SP3 32 bit
SLES 9.0 SP3 64 bit
SLES 10 SP1 32 bit
SLES 10 SP1 64 bit 
============

Please, help me choose a driver that could correspond to ubuntu set up

thank you so much

---

### Post by psusi on 2008-11-16
None of them do, but if it is an Intel Matrix Storage, you don't need a special driver for it since it's not really hardware raid.  You just need to install the dmraid package.  See [https://wiki.ubuntu.com/FakeRaidHowto](https://wiki.ubuntu.com/FakeRaidHowto) for more information.

---

### Post by 007casper on 2008-11-17
thanks psusi... thank you so much... 

I was downloading 64 bit server version of ubuntu 8.10... it states ubuntu-8.10-server-amd64.iso... amd???

I got two quad Intel Xeon E5420 Harpertown for the mb (asus DSEB-D16)... that set up should be able to handle 64 bit right... I have looked at the mb manual cant find anything that states otherwise... then when I was downloading ubuntu 8.10 I saw amd... I got a bit confused

need help... I really appreciate it in advance

---

### Post by psusi on 2008-11-17
AMD came up with the architecture while Intel was off trying to push the Itanium.  Intel realized the error of their ways and licensed AMD's system.

---

### Post by 007casper on 2008-11-17
wow, I didnt know that... yeah, Intel Xeon E5420 Harpertown is 64bit... so I am going to use the ubuntu-8.10-server-amd64.iso... then, it shouldnt be a problem right?

---

### Post by psusi on 2008-11-17
Right.

---

