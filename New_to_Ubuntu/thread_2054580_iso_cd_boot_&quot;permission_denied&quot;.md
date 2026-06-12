---
title: "iso cd boot &quot;permission denied&quot;"
date: 2012-09-07
forum: New to Ubuntu
---

### Post by Sonoran Desert Rat on 2012-09-07
I am booting from a successfully burnt iso cd and have an interesting problem:
 
When I look at the cd in windows it says 0 bytes available and 0 bytes used. Is this because it won't recognize Linux?
 
If I autorun the cd with windows up it works. The autorun cd offers the option to install a proper booter, which I did, and offers to reboot for you.
 
When I boot from the cd I get this:
 
Permission denied
 
See log file: c:\docume~1\owner\locals~1\temp\wubi-12.04-rev269.log
 
So I guessed and uninstalled wubi and I am still getting the error. ](*,)

Wubi ran fine if really slow.

Nutz and Boltz:

OS Name    Microsoft Windows XP Professional
Version    5.1.2600 Service Pack 3 Build 2600
OS Manufacturer    Microsoft Corporation
System Name    LAPTOP
System Manufacturer    TOSHIBA
System Model    Portable PC
System Type    X86-based PC
Processor    x86 Family 6 Model 13 Stepping 6 GenuineIntel ~1496 Mhz
BIOS Version/Date    TOSHIBA Version 1.20, 4/28/2004
SMBIOS Version    2.3
Windows Directory    C:\WINDOWS
System Directory    C:\WINDOWS\system32
Boot Device    \Device\HarddiskVolume1
Locale    United States
Hardware Abstraction Layer    Version = "5.1.2600.5512 (xpsp.080413-2111)"
User Name    DELETED
Time Zone    DELETED
Total Physical Memory    512.00 MB
Available Physical Memory    124.52 MB
Total Virtual Memory    2.00 GB
Available Virtual Memory    1.96 GB
Page File Space    1.13 GB
Page File    DELETED

*I did set the BIOS to boot from cd, and it will, but I get the purple screen for a few seconds and then the error message I posted above.

edit: okay, brownish purple, lol.

---

### Post by Bashing-om on 2012-09-07
Ok I'll take a stab at this.
"See log file: c:\docume~1\owner\locals~1\temp\wubi-12.04-rev269.log" 
says this is a windows problem.
soooo.... when you boot the install cd from a cold start you get a windows error ?
that to me indicates that you have not set the priority in bios to boot the cd first...

please check and advise.[INDENT]regards <==BDQ
(wubi install; no knowledge, others will have to assist)
[/INDENT]

---

### Post by Sonoran Desert Rat on 2012-09-07
> **Bashing-om said:**
> Ok I'll take a stab at this.
"See log file: c:\docume~1\owner\locals~1\temp\wubi-12.04-rev269.log" 
says this is a windows problem.
soooo.... when you boot the install cd from a cold start you get a windows error ?
that to me indicates that you have not set the priority in bios to boot the cd first...

please check and advise.[INDENT]regards <==BDQ
(wubi install; no knowledge, others will have to assist)
[/INDENT]

Thank you for the attempt! I have checked my bios 3 times, you are the third person to ask me that :p. I am positive it boots from the cd.

---

### Post by Sonoran Desert Rat on 2012-09-07
:lolflag: Now I get this:
This kernal requires the following features not present on the CPU:
pae
Unable to boot - please use a kernel appropriate for your CPU

AND here is my boot priority (unchanged):

Boot Priority=CD-ROM->LAN->HDD->FDD
HDD Priority=Builtin HDD->PC Card
Network Boot Protocol=PXE

---

### Post by Bashing-om on 2012-09-07
Sonoran Desert Rat;

I have no experience with wubi, therefore of no direct help to you// 
But, I will offer one suggestion (if this has not been done already).
how bout downloading the normal desktop install .iso; burn it to cd, see that this boots up (verifying the cd drive is good).

                                 hth <==BDQ

---

### Post by Sonoran Desert Rat on 2012-09-07
Yeah, that's what I'm trying to boot from. It is an .iso file downloaded from one of the ubuntu sites mirrors and burnt to cd.

Any response is better than none when your frustrated. :) Thanks.

---

### Post by TheGuyWithTheFace on 2012-09-07
> **Sonoran Desert Rat said:**
> 
When I look at the cd in windows it says 0 bytes available and 0 bytes used. Is this because it won't recognize Linux?

No, I got the same message from  burned music cd. I think it's just windows saying you can't write to the cd. 

As for wubi, I have no idea.

---

### Post by Bashing-om on 2012-09-07
welp, maybe no consolation, but keep in mind "it is only a thing"...there are solutions.

Now back to fault isolation...how bout grabbing up the cd and taking it to a friend's computer ...see if it boots up there ??? If it boot up there fine, we know we have problem in our own house (so to speak).

                                      regards <==BDQ

---

### Post by Sonoran Desert Rat on 2012-09-07
> **TheGuyWithTheFace said:**
> No, I got the same message from  burned music cd. I think it's just windows saying you can't write to the cd. 

As for wubi, I have no idea.

Oh! That makes sense. I had already burned the iso when it said that. :)

> **Bashing-om said:**
> welp, maybe no consolation, but keep in mind "it is only a thing"...there are solutions.

Now back to fault isolation...how bout grabbing up the cd and taking it to a friend's computer ...see if it boots up there ??? If it boot up there fine, we know we have problem in our own house (so to speak).

                                      regards <==BDQ

While I would love to do that, unfortunately, I live in the middle of the desert (literally) and because we recently relocated I don't have that option currently. ;) . Wondering if I should try it at the local library or if that's a bad idea...?

---

### Post by Bashing-om on 2012-09-08
Not a bad idea/problem is ..will the librarian allow you to change the bios (if not set to boot first)/ Need to know it is not ur cd device that is bad !
[INDENT]hth <==BDQ

[/INDENT]

---

### Post by jerome1232 on 2012-09-08
> **Sonoran Desert Rat said:**
> :lolflag: Now I get this:
This kernal requires the following features not present on the CPU:
pae
Unable to boot - please use a kernel appropriate for your CPU


Sounds like your cpu doesn't support PAE, Xubuntu and Lubuntu both use non-pae kernels and should work.

---

### Post by Sonoran Desert Rat on 2012-09-08
> **jerome1232 said:**
> Sounds like your cpu doesn't support PAE, Xubuntu and Lubuntu both use non-pae kernels and should work.

Thanks! I will try Lubuntu then.

---

### Post by Sonoran Desert Rat on 2012-09-08
I will try Lubuntu then. It was suggested to me earlier. Thank you!

---

### Post by Sonoran Desert Rat on 2012-09-10
> **Bashing-om said:**
> Not a bad idea/problem is ..will the librarian allow you to change the bios (if not set to boot first)/ Need to know it is not ur cd device that is bad ![INDENT]hth <==BDQ

[/INDENT]

I am working on this.

---

### Post by Sonoran Desert Rat on 2012-09-10
Okay, I downloaded and burnt the lubuntu iso to cd and rebooted by cd and got a message that says the boot filename is not found. :(

Here is what is on the cd when I open it in windows to look at the files:

.disk
boot
casper
dists
install 
isolinux
pics
pool
preseed
autorun
md5sum
README.diskdefines
wubi

I believe the burnt cd is fine. Is it posible I'm using the wrong boot window to boot from cd or need to do something special to boot from cd?

edit: I checked my computer's website and I definately have it set to boot from cd!

edit: solving this thread, I am pretty sure ubuntu didn't work with my cpu #-o

---

### Post by Bashing-om on 2012-09-10
Sonoran Desert Rat;

  The thought of you giving up is distastful to me (I love ubuntu !) .....

Ubuntu should run on a x86 system ..albeit maybe from minimal install.
please consult the hardware compatability list here for starters:[http://linuxhcl.com/](http://linuxhcl.com/)

We will assist in any manner to get you up.

[INDENT]kind regards <==BDQ

[/INDENT]

---

### Post by Sonoran Desert Rat on 2012-09-11
> **Bashing-om said:**
> Sonoran Desert Rat;

  The thought of you giving up is distastful to me (I love ubuntu !) .....

Ubuntu should run on a x86 system ..albeit maybe from minimal install.
please consult the hardware compatability list here for starters:[http://linuxhcl.com/](http://linuxhcl.com/)

We will assist in any manner to get you up.

[INDENT]kind regards <==BDQ

[/INDENT]

):P I didn't give up! LOL I've been using the ubuntu site a lot and when I figured something out I solved the thread and started a new one..hope that was the correct thing to do? 

I am logged in on Lubuntu right now! Yay! Just got it up and very excited!

Thought I should post this too, belatedly: Something in my computer is pae which ubuntu won't work with, Lubuntu is working great!

---

