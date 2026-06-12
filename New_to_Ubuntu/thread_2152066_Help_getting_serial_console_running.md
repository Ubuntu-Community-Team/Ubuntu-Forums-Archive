---
title: "Help getting serial console running?"
date: 2013-06-06
forum: New to Ubuntu
---

### Post by feralape on 2013-06-06
I'm trying to get a serial console working (on linux) and connect to it from windows (trying putty and teraterm).  I have a null modem cable that is plugged into serial port of each (both only have 1 port)

I do this on linux (nothing is setup in inittab yet).
```
root@test:/var/log# /sbin/getty -L ttyS0 115200 vt100
```

No errors, no output.  I also tried ttyS1 and ttyS2.

Then I open Putty (or teraterm) and it opens, but I don't get any output from either linux (getty) or windows (putty).  I tried both 11520 and 9600 on both sides.

For troubleshooting I also tried this (on linux with getty running):

```
statserial /dev/ttyS0
```

It gives this output (doesn't change or update).

```
Device: /dev/ttyS0

Signal  Pin  Pin  Direction  Status  Full
Name    (25) (9)  (computer)         Name
-----   ---  ---  ---------  ------  -----
FG       1    -      -           -   Frame Ground
TxD      2    3      out         -   Transmit Data
RxD      3    2      in          -   Receive  Data
RTS      4    7      out         1   Request To Send
CTS      5    8      in          1   Clear To Send
DSR      6    6      in          1   Data Set Ready
GND      7    5      -           -   Signal Ground
DCD      8    1      in          1   Data Carrier Detect
DTR     20    4      out         1   Data Terminal Ready
RI      22    9      in          0   Ring Indicator
```

This is only thing I can find in /var/log related to serial :

```
[    0.000000] console [tty0] enabled
[    0.576339] serial8250: ttyS2 at I/O 0x3e8 (irq = 4) is a 16550A
[    0.596874] 00:08: ttyS2 at I/O 0x3e8 (irq = 4) is a 16550A
[    0.617041] 0000:00:03.3: ttyS0 at I/O 0x1240 (irq = 17) is a 16550A
```

I've been using this as a rough guide; but seems a bit out of date [last update was in 2003 and has some commands that are no longer in repo?]: [http://www.tldp.org/HOWTO/Remote-Serial-Console-HOWTO/index.html](http://www.tldp.org/HOWTO/Remote-Serial-Console-HOWTO/index.html)


Any suggestions on how to troubleshoot this? It's a bit frustrating due to lack of output from either side.  Is there any way to get more info to see what might be going on?  Any other diagnose programs that might be useful?

---

### Post by matt_symes on 2013-06-06
Hi

> (nothing is setup in inittab yet).

Ubuntu does not use inittab anymore - not since dapper drake.

Ditch that tutorial as it is ancient.

Take a look at 

[http://superuser.com/questions/458843/how-to-connect-to-ubuntu-using-serial-port](http://superuser.com/questions/458843/how-to-connect-to-ubuntu-using-serial-port)

and 

[https://help.ubuntu.com/community/SerialConsoleHowto](https://help.ubuntu.com/community/SerialConsoleHowto)

Does that get you closer ?

Kind regards

---

### Post by feralape on 2013-06-06
Great, thank you!  It's working now :)

biggest problem was I was a dork and had the wrong interface (was using ttyS0 instead of ttyS2 - I thought I tried then both, but guess not).  But those link were quite useful and helped me sort it out.  Thanks for your time, it's working beautifully now.

---

