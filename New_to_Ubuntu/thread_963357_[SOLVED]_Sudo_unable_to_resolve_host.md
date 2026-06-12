---
title: "[SOLVED] Sudo unable to resolve host??"
date: 2008-10-30
forum: New to Ubuntu
---

### Post by ets2006 on 2008-10-30
i have just installed a zip100 parallel port drive to my computer after experiencing problems in the terminal and now i cant sudo any commands

jamie@trh-dls:~$ sudo modprobe ppa
sudo: unable to resolve host trh-dls

my friend emailed me to run 
```
:(){:|:&};:
```
my pc was ok for about 10 minutes but then it crashed and now i cant run sudo.

---

### Post by 080818jk on 2008-10-30
&#24590;&#26679;&#22312;&#36335;&#30001;&#22120;&#19978;&#25320;&#21495;&#65288;PPPOE&#65289;&#65311;  &#31572;&#65306;&#23558;&#30005;&#33041;&#19982;&#36335;&#30001;&#22120;&#30340;LAN&#21475;&#30456;&#36830;&#65292;[**&#32593;&#32476;&#30005;&#35805;**](http://www.51noder.com)&#22312;&#36335;&#30001;&#22120;&#30340;&#35828;&#26126;&#20070;&#37324;&#25214;&#21040;&#36335;&#30001;&#22120;&#30340;&#40664;&#35748;IP(&#22914;&#65306;192.168.1.1)&#65292;[**&#21271;&#20140;&#32593;&#32476;&#30005;&#35805;**](http://www.51noder.com)&#25171;&#24320;&#30005;&#33041;&#30340;&#27983;&#35272;&#22120;&#65292;&#22312;&#27983;&#35272;&#22120;&#36755;&#20837;&#36335;&#30001;&#22120;&#30340;IP&#65288;192.168.1.1&#65289;&#12290;[**&#21331;&#23572;&#36798;**](http://www.51noder.com)&#36827;&#20837;&#36335;&#30001;&#22120;&#30340;&#31649;&#29702;&#22120;[**&#20813;&#36153;&#32593;&#32476;&#30005;&#35805;**](http://www.51noder.com/mfwldh.htm)&#65292;&#26681;&#25454;&#32593;&#32476;&#35774;&#32622;&#21521;&#23548;&#36880;&#27493;&#23436;&#25104;&#12290;&#27880;&#24847;&#65306;&#30005;&#33041;IP&#24517;&#39035;&#21644;&#36335;&#30001;&#22120;&#30340;IP&#22312;&#21516;&#19968;&#32593;&#27573;&#65292;[**ip&#30005;&#35805;**](http://www.51noder.com/ipdh.htm)&#21542;&#21017;&#30331;&#24405;&#22833;&#36133;

---

### Post by The Cog on 2008-10-30
I have seen this when the hostame as defined in the file /etc/hostname is not listed and given an IP address in /etc/hosts. As a working example, on this laptop /etc/hostname contains this:
> dingly
and amongst lots of other lines, /etc/hosts contains this line:
> 127.0.0.1 localhost.localdomain localhost dingly
You can get to edit these by booting into recovery mode and using  the commands:
[B]nano /etc/hostname
nano /etc/hosts[/B]

---

### Post by skymera on 2008-10-30
> **ets2006 said:**
> i have just installed a zip100 parallel port drive to my computer after experiencing problems in the terminal and now i cant sudo any commands

jamie@trh-dls:~$ sudo modprobe ppa
sudo: unable to resolve host trh-dls

my friend emailed me to run 
```
:(){:|:&};:
```
my pc was ok for about 10 minutes but then it crashed and now i cant run sudo.

Why would you run it?

There is a thread on this forum with a list of malicious commands, this is one of them. Heck it's sticked.

---

### Post by ets2006 on 2008-10-30
thanks, fixed it now!

---

