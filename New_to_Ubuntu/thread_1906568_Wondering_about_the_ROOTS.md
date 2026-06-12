---
title: "Wondering about the ROOTS"
date: 2012-01-09
forum: New to Ubuntu
---

### Post by flyfishingphil on 2012-01-09
In the process of trying to set up my Toshiba Thrive to usb connect to my laptop with Ubuntu on of the steps included running lsusb in terminal to determine how the device is listed. When I saw the results I wondered if part of the problem could be the number of ROOTS shown. Here are the results:

lsusb
[I]Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 002: ID 045e:00e1 Microsoft Corp. Wireless Laser Mouse 6000 Reciever
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 003: ID 0930:7100 Toshiba Corp. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 0bda:0158 Realtek Semiconductor Corp. USB 2.0 multicard reader
Bus 001 Device 002: ID 04f2:b070 Chicony Electronics Co., Ltd 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub[/I]

Note that there are a total of:

6 listings of ID 1d6b:0001 Linux Foundation root hub, and,

2 listings of ID1d6b:0002 Linux foundation 2.0 root hub

Are all of these necessary and, if not, should they and how would I remove the excess?

Thanks

---

### Post by Cheesemill on 2012-01-09
That looks fine.

root (in that context) just means that the devices are plugged into your computers USB ports or are linked to your motherboards USB subsystem.

---

### Post by flyfishingphil on 2012-01-09
OK Thanks. Just thought I'd check to make sure I hadn't installed wrong or something.
I'll mark it solved.

---

