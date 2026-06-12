---
title: "Ubuntu 14.04 with AMD HD7700"
date: 2014-11-23
forum: New to Ubuntu
---

### Post by mixer_ai on 2014-11-23
Hey

i'm quite new to Linux. I have installed Ubuntu 14.04 couple days ago. Installation was fine. But when I'm using it. It will crash after couple minnuts. The screen will froze and soon the monitor will turn black like no signal. Can't change to other tty
. It looks like caused by the graphic card. I'm using AMD HD7700

it was not like this bad before I installed couple package for web development. Like php5 stuff. I'm not sure if it is related. Just writing down whatever I have and hopping someone could help me out.

---

### Post by mixer_ai on 2014-11-23
Anyone?

I tried to install AMD catalyst today. Installatin was successfully. However, when I try to run catalyst. It will pop out an command window and soon it will dispear like nothing happened.

---

### Post by QIII on 2014-11-23
Hello!

What do you mean by "pop out a command window"?

How did you attempt to install the driver?

Is this a laptop or a desktop?

Could you please run

```
gksudo amdcccle
``` and post the results after CCC fails?


Thanks.

---

### Post by mixer_ai on 2014-11-26
For unknown reason, the installed catalyst 14.9 disappear last day... I  cant even find a file or anything in the system. So I'm trying to  re-install it. I'm reading the releas note right now. I get stuck with  the required package installation.
[LIST]
[*]
[LIST]
[*]gimp-help-en 
[*]gimp-help-common 
[*]XFree86-Mesa-libGL 
[*]libstdc++ 
[*]libgcc 
[*]XFree86-libs 
[*]fontconfig 
[*]freetype 
[*]zlib 
[*]gcc 
[/LIST]
  
[/LIST]

in this list, XFree86-Mesa-libGL, libgcc, XFree86-libs, freetype, zlib, gcc,   returned "Unable to locate package"



I'm  recording what I'm doing in case if any new Ubuntu user is facing the  similar issue. Of course, also waiting for someone to help.

From the result of my searching, it seems like a lot people have already post some guild on installing AMD catalyst on ubuntu 14.04. But not much people mentioned about how to install those packages. Maybe its some thing very easy and dummy to explain about. But I think there would be some people like me, have no idea at all...

---

### Post by mastablasta on 2014-11-27
to install drivers- get latest Ubuntu 14.04 version with. opensource driver should be installed by default. then open additional drivers and click to install the catalyst drivers.

or use CLi to install from repositories or to do it manually: [https://help.ubuntu.com/community/BinaryDriverHowto/AMD](https://help.ubuntu.com/community/BinaryDriverHowto/AMD)

---

### Post by mixer_ai on 2014-11-27
> **mastablasta said:**
> to install drivers- get latest Ubuntu 14.04 version with. opensource driver should be installed by default. then open additional drivers and click to install the catalyst drivers.


or use CLi to install from repositories or to do it manually: [https://help.ubuntu.com/community/BinaryDriverHowto/AMD](https://help.ubuntu.com/community/BinaryDriverHowto/AMD)

Thanks for reply!

After a lot searching...I still can't find those packages. The only thing I know is they changed names.

So I review this artical. I tried before. Was stuck at aticonfig --initial

But this time I figure out why.

You need to apply this command first
 sudo /usr/lib/fglrx/switchlibGL amd

Then reboot your system. It may get freezed at login logo,
Then go to tty1 by ctrl-alt-f1
Login and try the aticonfig --initial again.

It should work and select amd

Then reboot again you will get the amd driver

---

