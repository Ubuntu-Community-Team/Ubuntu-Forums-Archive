---
title: "Puppy recognizes modem-Ubuntu doesn't"
date: 2008-08-03
forum: New to Ubuntu
---

### Post by GBPackerFan on 2008-08-03
Hi.  I've been trying both Puppy Linux and Ubuntu.  Both recognize most of my hardware, etc.  Puppy Linux recognizes my GTW v.92 Voicemodem, which I see is also referred to as a Broadcom v.92 4212 Softmodem, but Ubuntu doesn't.  How can I get Ubuntu to know what Puppy already does about my modem?  In looking around, it seems the usual answer is 'get an external modem'.  I'd rather not do that.  Thanks.

---

### Post by ibuclaw on 2008-08-03
With modems, it is best to use setserial.

```
sudo apt-get install setserial
```
And then run
```
setserial -g /dev/ttyS[01]
```
to query your modem.

if you get an output like this:
> 
/dev/ttyS0, UART: 16550A, Port: 0x03f8, IRQ: 4
/dev/ttyS1, UART: 16550A, Port: 0x02f8, IRQ: 3


Then Ubuntu has detected your modem alright, so you just create a link from ttyS0 to /dev/modem
```
sudo ln -s /dev/ttyS0 /dev/modem
```

Then you will probably need wvdial to get connected, do you know how to use it?

Regards
Iain

---

### Post by GBPackerFan on 2008-08-04
Ignore the reply below.  I found the setserial package by googling setserial and installed it.  My modem is now recognized.  I also installed minicom and it initialized my modem(!!) but how do I dial?  I'll keep searching when I have time.

Thanks for the reply.  When I type the 
sudo apt-get install setserial 
command in a terminal window, I get

Reading package lists...Done
Building dependency tree
Reading state information...Done
E:Couldn't find package setserial

What can I do to fix that error?

---

### Post by GBPackerFan on 2008-08-06
I did what was suggested (thanks), and I did get the results from setserial listed.  I then set up a wvdial.conf with the appropriate info, following several examples.
When I dial I get the following:

Sending ATZ
Sending ATQ0   (only part of the second init string)
Resending ATZ
Modem not responding

What can I do to debug this?  Can I turn on modem sound to see if anything is happening?  Help.

---

### Post by GBPackerFan on 2008-08-31
I was able to connect using broadband and loaded the many updates to Ubuntu.  I guess I will just update when I am able to find a broadband connection.

---

### Post by appier on 2008-08-31
Before you give up, try the instructions beginning at the following page on the Ubuntu Documentation:

[https://help.ubuntu.com/8.04/internet/C/modem-identify.html](https://help.ubuntu.com/8.04/internet/C/modem-identify.html)

---

