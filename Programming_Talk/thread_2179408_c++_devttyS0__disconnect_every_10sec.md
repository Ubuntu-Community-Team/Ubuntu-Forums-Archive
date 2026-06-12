---
title: "c++ /dev/ttyS0  disconnect every 10sec"
date: 2013-10-08
forum: Programming Talk
---

### Post by giorgiofoga on 2013-10-08
I have successfully created a complex application with QT C + + in ubuntu 12.04 32bit (AD255 itx motherboard). I used a connection of RS232 Modbus /dev/ttyS0 but had some problems. So now I use / dev/ttyUSB0 successfully.

as a test I have compiled[ATTACH]246813[/ATTACH] correctly a simple connection with libmodbus in C + +. The attach.

Libmodbus works well. / dev/ttyS0 does not work well.

But when I turn on the PC for 30 minutes, the Modbus connection is interrupted about every 10 seconds and about 10 seconds later resumed. After 30 minutes everything works ok.

If you use / dev/ttyUSB0 instead of S0, the program does not have this problem.

The problem is only after turning on the PC. After 30 minutes no longer occurs.


I need some explanation ....

---

