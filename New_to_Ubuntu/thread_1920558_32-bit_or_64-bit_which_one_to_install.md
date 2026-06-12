---
title: "32-bit or 64-bit which one to install"
date: 2012-02-05
forum: New to Ubuntu
---

### Post by ask_ on 2012-02-05
Hello , I have the following laptop :-
Lenovo Essential G Series G560
with the following specs :- 
```
PROCESSOR
Processor	Core i3
Variant	370M
Chipset	Mobile Intel HM 55 Express
Brand	Intel
Clock Speed	2.4 GHz
Cache	3 MB
MEMORY
Expandable Memory	Upto 8 GB
Memory Slots	2 (Unused Slot - 1)
System Memory	2 GB DDR3
STORAGE
Hardware Interface	SATA
RPM	5400
HDD Capacity	500 GB
OPTICAL DISK DRIVE
Optical Drive	Tray-in Rambo drive
PLATFORM
Operating System	Free DOS
DISPLAY
Screen Size	15.6 Inch
Resolution	1366 X 768 Pixels
Screen Type	HD LED Glare Display
INPUT
Web Camera	0.3 Megapixel
Pointer Device	Touchpad
Keyboard	Standard Keyboard
AUDIO
Internal Mic	Yes
Speakers	Yes
COMMUNICATION
Ethernet	10/100/1000M LAN
Wireless LAN	802.11 b/g/n
Bluetooth	v2.1
POWER
Battery Backup	Up to 3 hours
Power Supply	65 W AC Adapter
Battery Cell	6 Cell Lithium-ion
PORTS/SLOTS
USB Port	Yes
Mic In	Yes
RJ45 LAN	Yes
VGA Port	Yes
Multi Card Slot	Yes

```

Which version of Ubuntu 11.10 should I install 32-bit or 64-bit ?

Is it ok if one installs 32-bit version on 64-bit ?

And if I install 64-bit version are most of the common softwares available to run on it (I am talking about vlc player, etc) ?

In general how to judge by looking at the specs whether the computer is suited for 64-bit or 32-bit ?

From what I gather , 64-bit OS is for AMD processors and 32-bit is for Intel processors. Is my guess right , and what about the Intel i3 processor ?

(I am really apprehensive about installing 64-bit , I hope my PC doesn't support it :) )
Thanks.

---

### Post by donkyhotay on 2012-02-05
64bit OS is for 64 bit processors, intel and AMD are irrelevant as they both make 32 and 64 bit processors. if your processor is 64bit then use a 64bit OS, otherwise use 32bit OS. using a 32bit OS on a 64bit processor will work but you won't be able to use more then about 4gb of ram. for more info try google or wikipedia.
[http://en.wikipedia.org/wiki/64_bit#Pros_and_cons](http://en.wikipedia.org/wiki/64_bit#Pros_and_cons)

---

### Post by ask_ on 2012-02-05
> **donkyhotay said:**
> 64bit OS is for 64 bit processors, intel and AMD are irrelevant as they both make 32 and 64 bit processors. if your processor is 64bit then use a 64bit OS, otherwise use 32bit OS. using a 32bit OS on a 64bit processor will work but you won't be able to use more then about 4gb of ram. for more info try google or wikipedia.
[http://en.wikipedia.org/wiki/64_bit#Pros_and_cons](http://en.wikipedia.org/wiki/64_bit#Pros_and_cons)

Thanks. I don't intend to use more than 4gB RAM. Any ways the processor I have is the following :-
```
Processor	Core i3
Variant	370M
Chipset	Mobile Intel HM 55 Express
Brand	Intel
Clock Speed	2.4 GHz
Cache	3 MB
```

It can deal with RAM of 8GB so I am guessing it is 64 - bit PC . Right ? So I should go with 64-bit OS ? Are most software available for it ? And I am a beginner in programming C and Java, as a beginner will I have to right different programs for it ?

By the way , thanks for helping out.

---

### Post by 3rdalbum on 2012-02-05
> **ask_ said:**
> Thanks. I don't intend to use more than 4gB RAM. Any ways the processor I have is the following :-
```
Processor	Core i3
Variant	370M
Chipset	Mobile Intel HM 55 Express
Brand	Intel
Clock Speed	2.4 GHz
Cache	3 MB
```

It can deal with RAM of 8GB so I am guessing it is 64 - bit PC . Right ? So I should go with 64-bit OS ? Are most software available for it ? And I am a beginner in programming C and Java, as a beginner will I have to right different programs for it ?

Yes, the i3 is 64-bit.

Unlike in Windows, 64-bit is a "solved problem" in Linux. A Linux system consists mostly of open-source software that runs on eleven different exotic CPU architectures and has no trouble running on plain old 64-bit x86 either :-)

Even the stuff that's not open-source on Linux is usually either available as a 64-bit package, or runs in 32-bit compatibility mode easily enough.

64-bit is where you want to go. For certain tasks you'll see a speedup, and if you do decide to get another 2 GiB of RAM or more you'll be able to use all of it out-of-the-box.

If you've already downloaded 32-bit Ubuntu, don't worry too much. 32-bit operating systems also work perfectly well on 64-bit processors.

---

### Post by ask_ on 2012-02-05
> **3rdalbum said:**
> Yes, the i3 is 64-bit.

Unlike in Windows, 64-bit is a "solved problem" in Linux. A Linux system consists mostly of open-source software that runs on eleven different exotic CPU architectures and has no trouble running on plain old 64-bit x86 either :-)

Even the stuff that's not open-source on Linux is usually either available as a 64-bit package, or runs in 32-bit compatibility mode easily enough.

64-bit is where you want to go. For certain tasks you'll see a speedup, and if you do decide to get another 2 GiB of RAM or more you'll be able to use all of it out-of-the-box.

If you've already downloaded 32-bit Ubuntu, don't worry too much. 32-bit operating systems also work perfectly well on 64-bit processors.

Thanks for replying , that information was really useful.

No I haven't downloaded it yet , will do so.
By the way , what holds for Ubuntu 64-bit also holds for Lubuntu 64-bit ? 
Because , I am not too interested in the Unity desktop , I personally like the LXDE hence was thinking of using Lubuntu.
I like the low power usage of Lubuntu. And am not too enamored by 3-D effects and the like for desktop . I like to keep things clean and simple.

:guitar:

---

### Post by mcduck on 2012-02-05
> **ask_ said:**
> Thanks for replying , that information was really useful.

No I haven't downloaded it yet , will do so.
By the way , what holds for Ubuntu 64-bit also holds for Lubuntu 64-bit ? 
Because , I am not too interested in the Unity desktop , I personally like the LXDE hence was thinking of using Lubuntu.
I like the low power usage of Lubuntu. And am not too enamored by 3-D effects and the like for desktop . I like to keep things clean and simple.

:guitar:
Yes, apart from the user level stuff like default desktop environment and installed applications, all Ubuntu versions are one and the same operating system. The only difference is what DE & apps you get installed out-of-the-box.

---

### Post by ask_ on 2012-02-05
> **mcduck said:**
> Yes, apart from the user level stuff like default desktop environment and installed applications, all Ubuntu versions are one and the same operating system. The only difference is what DE & apps you get installed out-of-the-box.

That's great , thanks.

One more question - 
On that pros and cons page of 64-bit on wikipedia , it was given that programs need to make use of 64-bit pointers . So does this mean 64-bit programs will eat more memory. In that case , would a 2GB RAM give same performance as 1GB RAM :( . And to make full use of such processors therefore one has to go for 8GB RAM and so on ?

---

### Post by anewguy on 2012-02-05
Don't worry about that.  I would really, if I were you, just install it.  If this PC has Windows of some sort, you may want to make it dual-boot for a while.  Also, check things like wireless and video adapters to be sure the driver is either included with Ubuntu or is available (and preferably downloaded by you and ready to install prior to actually installing Ubuntu).

Dave ;)

---

### Post by 3rdalbum on 2012-02-05
> **ask_ said:**
> That's great , thanks.

One more question - 
On that pros and cons page of 64-bit on wikipedia , it was given that programs need to make use of 64-bit pointers . So does this mean 64-bit programs will eat more memory. In that case , would a 2GB RAM give same performance as 1GB RAM :( . And to make full use of such processors therefore one has to go for 8GB RAM and so on ?

Only the pointers and some numbers use more RAM, so no it's not double the RAM usage in total.

I'll just point out that you can install the LXDE desktop on Ubuntu, and the Unity desktop on Lubuntu. The only difference between Ubuntu and Lubuntu is the desktop, and it's very easy to install multiple desktops and switch between them at the login screen.

---

### Post by ask_ on 2012-02-05
Thanks everyone for the valuable tips.

---

### Post by mcduck on 2012-02-05
> **3rdalbum said:**
> Only the pointers and some numbers use more RAM, so no it's not double the RAM usage in total.

I'll just point out that you can install the LXDE desktop on Ubuntu, and the Unity desktop on Lubuntu. The only difference between Ubuntu and Lubuntu is the desktop, and it's very easy to install multiple desktops and switch between them at the login screen.

In addition to that, a 64-bit system will be able to use the larger amount (and larger in size) registries on the CPU which will increase performance.

(besides, using more RAM doesn't decrease performance, at least as long as you're not running out of available RAM)

...and of course the support for more memory addresses (and thus more RAM) is just one of the benefits 64-bit system has over a 32-bit one. It sure wasn't designed just because people needed more memory, there are many tasks that get a decent (or sometimes even quite impressive) boost from the 64-bit system's ability to handle larger numbers and higher precisions without requiring breaking the task into multiple steps. Basic apps like word processors and web browsers of course don't benefit from this, but if you do any audio/video processing, compression, transcoding, 3D rendering or similar tasks with your machine (and the program you are using is made to be able to benefit from 64-bit computing) the performance will be much better on a 64-bit system.

---

