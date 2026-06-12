---
title: "Which variant would be best?"
date: 2014-08-31
forum: New to Ubuntu
---

### Post by bobmac on 2014-08-31
Folks,
Because I'n no expert I have been running version 12.04LTS on my laptop.I have noticed recently that it has got very slow (only 1Gb RAM). I wonder if anyone can tell me if I'd be better off installing xubuntu or lubuntu. I don't do anything fancy with my machine mainly internet searches and such like.
I have no idea what the diffences are between xubuntu and lubuntu.

Also,which ever variation is best, can I install it over ver 12.04 or do I need to delete the partition and start again.

Any help gratefully appreciated,

Bob

---

### Post by uRock on 2014-08-31
You can change from ubuntu to xubuntu or lubuntu by installing their respective *ubuntu-desktop package via the terminal or Ubuntu Software Center, then logging out and clicking the ubuntu icon by your login and selecting the xubuntu or lubuntu desktop.

If you were running ubuntu, then changing to xubuntu should be enough to bring life to your system.

For Xubuntu```
sudo apt-get install xubuntu-desktop
```If you don't want all of the extra applications that normally come with Xubuntu, then you may run the following, which will install just the things needed for XFCE desktop. Your ubuntu programs will still be in the menus.```
sudo apt-get install xfce4
```For the lubuntu desktop run,```
sudo apt-get install lubuntu-desktop
```Without the extra softwares,```
sudo apt-get install lxde
```
Cheers & Beers,
uRock

---

### Post by mastablasta on 2014-09-01
in this case it is probably not so much the issue of ram as it is of GPU. Xubuntu or Lubutnu would work better.

---

### Post by bobmac on 2014-09-01
Folks,

Many thanks for your information.
I tried to install xfce and xubuntu desktop and got the following messages:

calban@ubuntu-laptop:~$ sudo apt-get install xfce
[sudo] password for calban: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package xfce
calban@ubuntu-laptop:~$ sudo apt-get install xubuntu desktop
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package xubuntu
E: Unable to locate package desktop
calban@ubuntu-laptop:~$

Can youtell mewhat I've done wrong

Regards,

Bob

---

### Post by deadflowr on 2014-09-01
Try xfce4
The other package xubuntu-desktop, needs a dash.
Basically without the dash it thinks you asked for two separate, and non-existing, packages xubuntu and desktop.

Either/or as to which one you want to install.

---

### Post by bobmac on 2014-09-01
Deadflower,

You're not just helpful you're a genius.
Many thanks for your help and the help of the others that provided the information,you're all gurus in my book 

Regards,
Bob

---

### Post by mastablasta on 2014-09-01
also it's sudo apt-get install xubuntu[SIZE=5][COLOR=#FF0000]**-**[/COLOR][/SIZE]desktop not sudo apt-get install xubuntu desktop

---

### Post by Impavidus on 2014-09-01
Note that Xubuntu 12.04 LTS only has three years of support, instead of five years for Ubuntu. This means that about 7 months from now the Xubuntu-specific packages wil reach end-of-life.

---

### Post by didier5 on 2014-09-01
Here is my experience.

I have also installed Ubuntu 12.04 on 1Go RAM. + 1Go Swap. It was slow.

Then I looked at the statistics (browser firefox normal usage with youtube).  The Ram was never the bottleneck
 (let's say 75% on average) but the processor with frequent 100% peaks.

In my case, an extra 1Go Ram to totalise 2 Go would have been useless.

With Lubuntu ( I have not checked Xbuntu ), RAM is 25% and processor is 20%.
(Lubuntu 14.04.1)

---

### Post by mastablasta on 2014-09-02
that is because the CPU is doing the hardware 3D acceleration needed to draw Ubuntu Unity interface instead of the GPU doing all that work. 

Lubutnu has 2D interface and hence that kind of system resources are not needed. it doesn't look that pretty then though. :P

---

### Post by Vladlenin5000 on 2014-09-02
> **bobmac said:**
> I have noticed **recently** that it has got very slow (only 1Gb RAM). (my bold)

That single word made me think... Could yours be one of those cases of (recent) dropped support for some graphics cards/chips (AMD/ATI mostly)? 
Knowing your laptop specs would be good. Please post make/model, CPU, GPU, etc...

---

