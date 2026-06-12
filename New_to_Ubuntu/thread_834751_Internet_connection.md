---
title: "Internet connection"
date: 2008-06-19
forum: New to Ubuntu
---

### Post by Warren Sugden on 2008-06-19
I have recently installed (to run off DVD) "linux Starter Kit" - issue 104 April 2008 - LXF104D/o4/08 made in EU.    I think it is Ubuntu 8.04.

Everthing appears to work although I am not connected to the internet.

My computer presently runs XP home and is connected to the internet with external broadband modem SpeedTouch 530, however is not installed when i load Ubuntu.    There is no advise or direction as to connecting to internet.

How do I connect to internet  ??.    My ISP and modem supplier do not support Linux.   I'm told the DNS should be 210.15.254.240

Can anyone help.   I am totally new to Linux.

Warren Sugden

---

### Post by Delever on 2008-06-19
System->Administration->Network

Unlock

Open DNS tab, and enter this DNS address there.

Close.

Then try to open some web page.

---

### Post by Warren Sugden on 2008-06-19
I went to System\Administration\network but found no option to unlock, although there was a DNS Tab where I entered the DNS number, but still no connection to internet.

Any other help please ??.

Warren Sugden

---

### Post by plucky on 2008-06-20
> **Warren Sugden said:**
> I went to System\Administration\network but found no option to unlock, although there was a DNS Tab where I entered the DNS number, but still no connection to internet.

Any other help please ??.

Warren Sugden

Yes I think that is broken in Hardy.

In the top panel system tray there is an icon that look like two monitors,left click on that and select **manual configuration**. The Network window will open and you can then click on **Unlock**



Good Luck

---

### Post by Warren Sugden on 2008-06-20
Plucky

This gives exactly the same result as my earlier effort.   There is NO option to Unlock and i am unable to find any Unlock option anywhere.

Any further suggestions ????.

Warren Sugden

---

### Post by Pjotr123 on 2008-06-20
USB modems are nasty. Consider a router/modem combination that connects to your PC with a networking cable (ethernet). Always works and technically superior.  :-)

---

### Post by cariboo on 2008-06-20
Just so we know what version you are using could you type in a Applications-->Accessories-->Terminal:

```
uname -a
```

and paste the results in your nest post. To copy and paste the output just highlight the resulting line and then if you have a wheel mouse just click the wheel, if you have a two button mouse click both mouse buttons at the same time.

Jim

---

### Post by Warren Sugden on 2008-06-20
pjotr123

I have tried both USB and ethernet, but both produce the same result.   No internet connection

caribou907

the cut and paste did not work, but here is the result.

I got :
   linux ubuntu 2.6.22-14 generic #1 SMP Oct 14 23:05:12 GMT 2007   i686 GNU/linux

Warren Sugden

---

### Post by plucky on 2008-06-21
From a terminal please post the output of ```
lspci
lsusb
ifconfig
```

These commands will show us what in on your PCI interfaces,USB interfaces and your ethernet interface.

p.s You can copy and paste between workspaces,so if you have firefox open in one workspace and the terminal in another,you can copy the terminal output into firefox.Saves a lot of typing.

---

### Post by Pjotr123 on 2008-06-21
Maybe it's this:
[http://ubuntutip.googlepages.com/nointernetconnection](http://ubuntutip.googlepages.com/nointernetconnection)
(number 2 )

---

