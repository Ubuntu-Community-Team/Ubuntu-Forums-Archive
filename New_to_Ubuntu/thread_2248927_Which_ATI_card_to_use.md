---
title: "Which ATI card to use?"
date: 2014-10-18
forum: New to Ubuntu
---

### Post by steve164 on 2014-10-18
Good morning and hello.
Let me start from the beginning; I'm a complete Linux Noob so please be gentle and patient. I have recently dug out an old system I built for the kids back in 2007 running Wndows XP that had been unused for years. Rather than scrap it I decided to do something with it. Having discovered that MS have stopped all support for XP and Vista both of which I have genuine copies of I decided to look at Ubuntu. 
I went ahead and installed Ubuntu 14.4 64 bit but this morning I have messed something up by trying to get additional memory recognised after I upgraded the RAM from 3 to 4gb and changing graphic cards a couple of times. Anyway I'm about to do a full reinstall but before I do I want a more informed approach based on the spec of the machine I'm using which is here:
Asus A8R32-MVP Deluxe motherboard BIOS v0701
AMD Athlon 64 X2 4800+ 2.5 GHz @2.76
4Gb Elixir PC-3200 DDR 400 memory
300Gb SATA HD.

It was originally fitted with an ATi Radeon 2900XT but I then fitted a Radeon AX4870 1Gb but I couldn't find drivers for it. I also have an old Radeon X1900XT.

So I have three choices of graphics card to fit in the machine so I'd like some advice on which would be the most compatible.

I know this is a really low spec machine by current standards and it's not intended to replace my current system. This is a project and my way of discovering Ubuntu without spending a lot of money at this time. I have to say that being hitherto completely Windows based I found my recent brief experience of Ubuntu thoroughly refreshing albeit a challenge, very much like learning a new language.
So any help and advice will be most welcome.

Thank you.

---

### Post by mikewhatever on 2014-10-18
So, how much RAM does it recognize, and which card does it work best with? Old ATI cards don't have any proprietary drivers available, as AMD had dropped support for anything older then HD 5000, but the free driver should work. 
While the machine is still very capable, [Xubuntu]("http://xubuntu.org/getxubuntu/") might be more suitable.

---

### Post by Autodave on 2014-10-18
I would also recommend Xubuntu: much simpler screen and much less RAM usage.  As for 4 gig, that should be way more than enough for Xubuntu.

---

### Post by haplorrhine on 2014-10-18
My netbook has:
- up to 2.41 GHz
- 2 GB DDR3-L memory
- 320 GB hard drive
- Intel HD Graphics

It runs the standard Ubuntu 14.04 package just fine.  But I just do web browsing, math calculations, taking notes, etc.   When using Ubuntu 12.04, Audacity took about 10 minutes to apply a sound effect, but it takes about a minute with 14.04's improved kernel.

I would be more worried about things like whether the wifi card will be recognized.

---

### Post by Rob Sayer on 2014-10-18
According to this:

[https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)

all 3 cards you mentioned should work fine with the open source radeon driver used by ubuntu, including 3D acceleration in hardware.

As mentioned, don't bother with the proprietary fglrx ATI driver for those cards.

You should actually find Ubuntu with the Unity desktop OK with the 1Gb video card, but other DEs will run faster.  KDE is considered slow but you can really tweak it for speed.  Xubuntu will run quite fast too.

---

### Post by steve164 on 2014-10-18
Hello and thanks for the replies. I have just done a full reinstall from the Live CD and internet. This time Ubuntu has automatically found drivers for the ATi 4870: Gallium 0.4 on AMD RV770 as per the list of Radeon Drivers in Rob Sayer's link. Is there a way of adjusting the video card settings through the driver?
Strangely though it is still only reporting 2.9GiB of memory when there is 4GiB installed. Ubuntu does seem more responsive this time though.
I'm just working through some guides to tweaks and downloads for the install.
Very steep learning curve but thoroughly enjoying it.
Cheers,
Steve.

---

### Post by grahammechanical on 2014-10-18
For your information, Gallium 0.4 is the open source video driver and AMD RV770 is the AMD code name for the ATI 4870. System Settings has a Screen Displays utility that gives us some options. Every time we boot Linux/Ubuntu reads some information in the monitor called Extended Display Identification Data (EDID) and from that Ubuntu gets the optimum screen resolution. So, we do not need to do many adjustments.

The memory that you have is more than enough for Ubuntu 14.04. I only have 1GB RAM and the system is working fine. Mind you, I do have a video card with 1GB of its own memory. The power of the video card and the amount of memory it has can have a limiting effect on the user experience. But your set up can run Unity 3D. If it could not you would not be running on Gallium 0.4 but Gallium 0.4 llvmpipe, which is a version of the open source driver that Ubuntu uses for video cards that cannot do accelerated 3D rendering in hardware.

As regards the memory problem, does the BIOS report 4GB RAM?

Regards.

---

### Post by steve164 on 2014-10-18
> **grahammechanical said:**
> For your information, Gallium 0.4 is the open source video driver and AMD RV770 is the AMD code name for the ATI 4870. System Settings has a Screen Displays utility that gives us some options. Every time we boot Linux/Ubuntu reads some information in the monitor called Extended Display Identification Data (EDID) and from that Ubuntu gets the optimum screen resolution. So, we do not need to do many adjustments.

The memory that you have is more than enough for Ubuntu 14.04. I only have 1GB RAM and the system is working fine. Mind you, I do have a video card with 1GB of its own memory. The power of the video card and the amount of memory it has can have a limiting effect on the user experience. But your set up can run Unity 3D. If it could not you would not be running on Gallium 0.4 but Gallium 0.4 llvmpipe, which is a version of the open source driver that Ubuntu uses for video cards that cannot do accelerated 3D rendering in hardware.

As regards the memory problem, does the BIOS report 4GB RAM?

Regards.

Thanks Grahammechanical.
On the previous install I was indeed running the Gallium 0.4 llvmpipe version. 
 My ATi 4870 has 1GiB of RAM.
The BIOS reports the full 4Gib RAM: (1GiB matched chips in each of the four MB slots).
I have installed the 64 bit version Of Ubuntu 14.04 LTS. I corrupted the first install by trying to run before I could crawl. I did a bit of research and jumped in and installed the PAE Kernel in a vain attempt to fix the missing memory. The PAE Kernel is intended for 32 bit systems with more than 3GiB of memory and is not required for my set up as I quickly found out.... :redface:
Anyway it's up and running now and it seems far more responsive. I've got both a wired and wireless network running. The wireless dongle was picked up immediately and configured automatically. I just had to enter the wireless password. 
 I'm very quickly getting more and more drawn to the Ubuntu machine. My main system has Windows 7 but it's a long time since I've felt any sense of achievement or excitement with a PC. I really like the idea that I'm using something different than the masses, if that makes sense. 

Cheers,
Steve

---

### Post by Paulgirardin on 2014-10-18
I'm using an ASUS PK5-SE  with core 2 duo 2.66GHz,4 Gb ram,ATI graphics and it runs fine with Ubuntu Unity.No need to go for the lighter DEs

---

### Post by Sef on 2014-10-18
> [COLOR=#000000]Let me start from the beginning; I'm a complete Linux Noob so please be gentle and patient.[/COLOR]

If someone is not gentle and patient with you, please click the report post button at the bottom left of each post.

Thank you for being a part of Ubuntu.

---

### Post by steve164 on 2014-10-19
> **Sef said:**
> If someone is not gentle and patient with you, please click the report post button at the bottom left of each post.

 Thank you for being a part of Ubuntu.

Thank you for that; I'm confident it won't be necessary though:D 


I have fixed the missing memory issue by simply enabling "Hardware Memory Hole" in the BIOS Memory Configuration page. I now have 3.9GiB of memory showing in "System Details"
Really starting to get into my new Ubuntu OS. It is different to what I've become accustomed with Windows. However the transition from Windows 3.1 to 95 was a big leap and even using an iPad requires a learning curve.
Cheers,
Steve

---

### Post by Mike_Walsh on 2014-10-19
Hi, Steve.

I, too, consider myself a 'noob' (at least with Linux; been messing about with these things for 30 some-odd years). Only started back in May, but have quickly adjusted to the learning curve, and am enjoying myself more than I have done for years.

Even though my system is ten years old (formerly running XP), I was lucky in having the excellent Athlon 64; the first commercially-available processor that could natively run both 32- AND 64-bit applications without ANY input from the operator. The 64-bit version is indeed more responsive than the 32-bit version.....at least, it IS on my hardware. Which works SO well with Linux that I'm also running most of the other 'buntu flavours, too!

Welcome to the community, and.....have fun! :p

Regards,

Mike.

---

