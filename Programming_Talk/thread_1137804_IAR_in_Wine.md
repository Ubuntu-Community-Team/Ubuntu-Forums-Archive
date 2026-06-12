---
title: "IAR in Wine?"
date: 2009-04-25
forum: Programming Talk
---

### Post by lowbagger on 2009-04-25
Hi,

I am having a heckuva time getting C code to compile and load onto my MSP430.  I have had zero success getting mspgcc or cdk4msp to work.  I have tried Eclipse too (with the CDT package), but I find it even more difficult to understand.  I have just managed to get IAR to run in Wine, but it won't talk to my parallel port.  I confess that I am sort of a Linux newbie, so could someone tell me how I can debug my MSP code on the board itself, using the parallel-JTAG connector?  

I suspect the problem is something as simple as knowing how to set the right permissions on the parallel port.  I can do ls -l /dev/lp0 and I get

crw-rw---- 1 root lp 6, 0 2009-04-25 14:28 /dev/lp0.

This means that only root can read and write to it and nobody can execute, right?  How do I change this?  

Sorry for such a stupid question, but I'm in a real jam here.  I have to get my converter working by Thursday or I'm hosed.

Thanks,

Lowbagger

---

### Post by Zugzwang on 2009-04-26
First of all, when using abbreviations which are uncommon here (IAR?), please state what they mean. Than increases the likelihood of answers significantly. ;-)

As far as the parallel port is concerned, first of all make sure that you have no programs/daemons/whatever running that are actually accessing them. I must admit that I have no clue how to check this.

For changing the permissions, change the file permissions to "777":
```

sudo chown 777 /dev/lp0

```
However, this is not a good solution to the problem. In particular, it gives access to the port to everyone on your machine! It is better to create a special group for the parallel port, to add yourself to the group and then change the ownership of lp0 to that group.

I'm not sure if that will actually help you! Also, the changes might or might not vanish when rebooting. 

Note that there are also WINE setting for the serial/parallel port, you might want to have a look at them.

Good luck!

---

### Post by lowbagger on 2009-04-26
Thanks.  

IAR is development software - the package is called IAR Embedded Workbench - and I have no clue what IAR stands for.  Sorry.

---

### Post by tormod on 2010-01-07
See also [http://www.winehq.org/pipermail/wine-users/2007-May/027308.html](http://www.winehq.org/pipermail/wine-users/2007-May/027308.html) and [http://www.goodbyemicrosoft.net/news.php?extend.403](http://www.goodbyemicrosoft.net/news.php?extend.403)

---

