---
title: "not jumping ship, going to work through this."
date: 2016-06-13
forum: New to Ubuntu
---

### Post by Amelia_Hayner on 2016-06-13
decided after more reading that I do not need another puppy in my life- going to figure out how to make Ubuntu 14.04 work nicely with me.
problem- it is impossibly slow. I update software as it asks me to... but something must be wrong. pages time out before they load.
I have an older computer, about 10 years old, possibly there is a forum for people like me?
it is asking me to update now, and I am afraid to, it seems to get worse every time.

---

### Post by jimmy-frydkaer on 2016-06-13
Have you tried Lubuntu which is better on old computers like the one you mentioned?

---

### Post by Amelia_Hayner on 2016-06-13
no, have not. open to the suggestion, though! will it install easier with the ubuntu already on computer now? I SO don't want to go back to scratch, I completely wiped windows off and ubuntu is now the only system on here. I don't have a whole lot of time available right now to obsess over this!!

---

### Post by oldrocker99 on 2016-06-13
Lubuntu, Xubuntu and Ubuntu MATE, all lightweight, install just the same way. To add a different desktop without reinstalling from scratch:```
sudo apt-get install lubuntu-desktop
```

Or:```
sudo apt-get install xubuntu-desktop
```

Or:```
sudo apt-get install mate-desktop
```
You can select the desktop from the login screen (otherwise known as the display manager).

I prefer MATE myself, but all three are lightweight and are suitable for a ten year old computer.

---

### Post by kurt18947 on 2016-06-13
It's likely that a 10 year old machine would be 'happier' with a less graphically demanding *buntu variety. Lubuntu, Xubuntu, LXLE (Lubuntu spin with useful additions) and others. The installer is the same on Xubuntu & Lubuntu as it is on Ubuntu so no leaps there. I think LXLE is the same also but I'm not positive, it's been some time since I installed LXLE. I suspect that one of the options present when installing *buntu would be to overwrite the existing installation.

---

### Post by steeldriver on 2016-06-13
"pages time out before they load" sounds like a networking problem, specifically

---

### Post by pfeiffep on 2016-06-13
> **Amelia_Hayner said:**
> decided after more reading that I do not need another puppy in my life- going to figure out how to make Ubuntu 14.04 work nicely with me.
problem- it is impossibly slow. I update software as it asks me to... but something must be wrong. pages time out before they load.
I have an older computer, about 10 years old, possibly there is a forum for people like me?
it is asking me to update now, and I am afraid to, it seems to get worse every time.
I'm using a 6 yr old computer  also and have found that Ubuntu with unity is pretty sluggish. When using Ubuntu 14.04 LTS I found a less resource hungry desktop environment - **_gnome flash back_** is available to install for you.
Rather than another puppy you might consider installing some more ram memory.
I have replaced Ubuntu 14.04 LTS with Ubuntu MATE 16.04 LTS and have no issue with slowness

---

### Post by Geoffrey_Arndt on 2016-06-13
First area to check out is have you made any browser changes ( . . . changed settings) or any other internet device changes (new modem, new router, new ISP)?   Do you live in  an area with bandwidth restrictions?   Do you still have adequate disk space on the computer?

So, the above questions goto the issue of "network" (as Steeldriver mentioned).

One final point, . . . to help us understand your situation better . . .rather than telling us you have an old computer (which may NOT be the issue at all) . . . tell us the specs of your computer:

>   Make
>   Model
>   What version of Ubuntu?
>   What Desktop Environment (Unity, Mate, XFCE, etc.)
>   Ram amount (512 KB or 1, 2, 4, 8 16 GB ?)
>   What kind of video system (nvidia xxx, ati xxx, intel xxx)?
>   How large is your Hard Drive and how much of that did you allow for Ubuntu?

These kind of questions/answers help to narrow down the rather nebulous information many posters present in their requests for help.

---

### Post by grahammechanical on 2016-06-13
If you are serious about working through this, then please open About This Computer from the power/cog drop down menu. That will open System Settings at the Details page. What does the Details page list under Graphics?

If it says llvmpipe, then that would indicate that the issue is a proprietary video driver or a lack of one. Ubuntu uses llvmpipe when the video adapter cannot run Unity 3D and when there is a conflict with a proprietary video driver. Llvmpipe is an open source video driver that gives an approximation of Unity 3D but it is slow even on video adapters that can run Unity 3D.

The latest proprietary video drivers drop support for older video adapters. I cannot run the latest Nvidia drivers because they do not support my Nvidia GT220 any mode. If I want to use an Nvidia driver I have to use a legacy version. Actually, I use the open source video driver for Nvidia adapters. It is called Nouveau. And Unity is reasonably fast.

So, that is one area to check. I can also confirm the benefit of installing gnome-session-flashback, as recommended. That will give us two additional log in options. Gnome Flashback (Compiz) which will not seem much faster and Gnome Flashback (Metacity) which is definitely faster because Metacity uses less memory than Compiz and it does not require the video adapter to do accelerated 3D graphics that is required by the combination of Compiz and Unity 3D.

Regards.

---

### Post by Bashing-om on 2016-06-13
Amelia_Hayner; Hello;

Not a thing I can add to the excellent suggestions offered.
I will try and bolster your confidence in older hardware . I too run an old system .. 2007 AMD with but 4 Gigs of ram.
I have absolutely no problems . However, a lighter desktop does run faster than that of unity ( default DE for ubuntu).

A bit more muscle
[INDENT][INDENT]will do wonders
[/INDENT][/INDENT]

---

### Post by JayKay3OOO on 2016-06-13
I have a 2006 macbook pro. It became incredibly slow by 2014. 

I backed up my work, brought a new hard drive, put the OS back on and boom. Back to good old happy snappy snowy self. The storage drive does slow down after 5+ years and a slow hard drive can destroy performance making once usable machines time sucking leeches that seem to do nothing as they hunt for files on their bad sectored and slow drives.

Don't forget about ubuntu  mate edition that is similar to old gnome in resource use.

Be careful though as doing ram and hard drive upgrades on an old machine can escalate quickly especially if you take it to a shop to do it for you. Then the benefit of buying a new machine becomes worthwhile.

---

### Post by Amelia_Hayner on 2016-06-13
> **steeldriver said:**
> "pages time out before they load" sounds like a networking problem, specifically

I don't think so, because we do have DSL here. we watch movies on streaming, (not from this computer, but from the wireless box) and when Ubuntu was first installed it was like WONDERFUL, I could watch youtube videos, etc. but no more.

oooh this is scary.... BTW- all the info asked for, amount of RAM etc .... where would I find that??

---

### Post by oldrocker99 on 2016-06-13
Please post the results of```
lspci
``` and ```
free
```

The first will show everything on your motherboard, and the second shows how much RAM you have.

And welcome to the forums! This is what a lot of us love to do, help newbies.

The note above about old hard drives may be relevant.

---

### Post by Amelia_Hayner on 2016-06-13
I think it's supposed to rain Thursday so maybe I can stop tending to the yard and work on this. Thanks for all the many answers! I am sure one of them will work.

here is the result of the lspci command:
```
amelia@amelia-CM5570:~$ lspci
00:00.0 Host bridge: Intel Corporation 4 Series Chipset DRAM Controller (rev 03)
00:02.0 VGA compatible controller: Intel Corporation 4 Series Chipset Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation 4 Series Chipset Integrated Graphics Controller (rev 03)
00:1a.0 USB controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #4
00:1a.1 USB controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #5
00:1a.2 USB controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #6
00:1a.7 USB controller: Intel Corporation 82801JI (ICH10 Family) USB2 EHCI Controller #2
00:1b.0 Audio device: Intel Corporation 82801JI (ICH10 Family) HD Audio Controller
00:1c.0 PCI bridge: Intel Corporation 82801JI (ICH10 Family) PCI Express Root Port 1
00:1c.5 PCI bridge: Intel Corporation 82801JI (ICH10 Family) PCI Express Root Port 6
00:1d.0 USB controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #1
00:1d.1 USB controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #2
00:1d.2 USB controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #3
00:1d.7 USB controller: Intel Corporation 82801JI (ICH10 Family) USB2 EHCI Controller #1
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 90)
00:1f.0 ISA bridge: Intel Corporation 82801JIB (ICH10) LPC Interface Controller
00:1f.2 IDE interface: Intel Corporation 82801JI (ICH10 Family) 4 port SATA IDE Controller #1
00:1f.3 SMBus: Intel Corporation 82801JI (ICH10 Family) SMBus Controller
00:1f.5 IDE interface: Intel Corporation 82801JI (ICH10 Family) 2 port SATA IDE Controller #2
01:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 01)
02:00.0 Network controller: Ralink corp. RT2790 Wireless 802.11n 1T/2R PCIe
amelia@amelia-CM5570:~$
```

here is the result of the command "free":
```
amelia@amelia-CM5570:~$ free
             total       used       free     shared    buffers     cached
Mem:       6076112    2189036    3887076     271728     150276    1078016
-/+ buffers/cache:     960744    5115368
Swap:      6253564          0    6253564
amelia@amelia-CM5570:~$
```

---

### Post by Bashing-om on 2016-06-16
Amelia_Hayner; Hey !

With 6 Gigs of on-board ram, you should have no problem running whatever suits your fancy. The graphic's are Intel and again well supported out of the box.

I suggest we find out why there are present problems with the 14.04 install.
Is this "slow" noticed system wide ? Or only in particular application(s) ?
Does the system boot up normally ?
If you boot up a liveDVD(USB) is the performance there satisfactory ?

We seek to find a common point to start the troubleshooting from.

[INDENT][INDENT]got to be a cause
[/INDENT][/INDENT]

---

### Post by Amelia_Hayner on 2016-06-16
THANK YOU for reading through that gibberish.
well, I am not sure if it boots normally. It goes through the BIOS page every time. goes fairly quickly, I thought maybe it was supposed to do that.
the applications that are the slowest that I notice are anything to do with a video.
at first, when I start it- it goes well, then quickly slows down to a crawl.
good to know there might be a fix to this. 
( I don't do any sort of gaming, and the only thing husband does on here is play solitaire or mahjong. But I LOVE to watch funny animal videos)
what sort of live DVD would you want me to try.. ??

---

### Post by Bashing-om on 2016-06-16
Amelia_Hayner; Well ..

IRT bios:
> 
It goes through the BIOS page every time.

There are settings in bios to not display posting and/or memory testing . IF you are to mess about in bios, be aware of what you are doing and take plenty of notes ! Good thing is that there are provided means to revert to default or optimum settings if one hoses up bios to the point of no return . ( been there, done that ) 

If the only difficulty is in playing video, I would question the application it's self . 

Is the utility for videos ' avconv ' // or generally the slow down also from within the browser ?

As to testing with a live environment, in your case I would suggest the same as you have installed .

[INDENT][INDENT]not so bad
[INDENT][INDENT][INDENT]after all
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by Amelia_Hayner on 2016-06-27
well, things are not going well here as I am writing this on the tiny keyboard of the KINDLE. I succumbed to the little dancing "update your soft ware" and as I feared- everything has slowed to a glacial pace. there seems to be a problem with firefox and adobe flash, even though I let the thing run ALL DAY sat.  it did not install. so. I have ordered a live DVD for MATE which should be here in a few days. I hope it`s so lively it tapdanced when I open the container. If it works I will send alms to tbe website via PayPal. stay tuned, I am sure you will hear more from me.

---

### Post by kurt18947 on 2016-06-27
Hey Amelia-

If you're bored in the meantime here are a couple apps that might provide insight into what is slowing things down for you. One that I find most informative as far as cpu & RAM usage is HTOP. It should be available in the repositories. Once installed (it's very light) you can either use the windows/super key or terminal and type 'htop'. This runs in a terminal windows so should work on any desktop. The application using the most resources (Firefox for me right now) will be at the top of the list and stationary. Another app I use is 'system monitor' installed by default in Ubuntu-Gnome and I suspect Ubuntu. Clicking on the 'processes' tab will show what apps are using what resources.

---

### Post by Amelia_Hayner on 2016-06-27
thank you. please don't go anywhere I will need you in a couple of days!!!

---

