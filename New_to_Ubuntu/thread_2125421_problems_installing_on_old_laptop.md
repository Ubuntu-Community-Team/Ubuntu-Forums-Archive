---
title: "problems installing on old laptop"
date: 2013-03-13
forum: New to Ubuntu
---

### Post by billbobagwell on 2013-03-13
hey, i am new to ubuntu. I decided to finally try to escape the windows world, so i searched around and thought lubuntu looked pretty interesting. Never using anything besides windows i decided to try lubuntu on an ol' cheapie. so here's my problem.  i have a toshiba satellite 1800-s203 with 800mhz intel celeron, 256mb ram, 40 hd and a 8mb Trident Microsystems Cyber-blade AI1 video chip. When i try to install it will begin, blue screen with Lubuntu 12.10 loading, then after about 5mins it goes black with lubuntu 12.10 still loading and finally it just goes black. I've tried nomodeset but still nothing:( please help!

P.S. I have a feeling it may have something to do with the graphics chip being how its kinda an out there old card

okay now it went to the black loading screen and said *starting *starting *stopped and then nothing again

---

### Post by Mr. Shannon on 2013-03-14
Are you using the regular install disk or the alternate installer. The regular installer requires more memory than you have available.  That graphics card may also be an issue: here is a really old thread dealing with that issue ([http://ubuntuforums.org/showthread.php?t=806835](http://ubuntuforums.org/showthread.php?t=806835)). I have no idea whether this will work for you or not.

To be honest, as a first step into the world of linux you are adding a lot of hardship to yourself by attempting to use such an old machine with a modern operating system. I hope this does not discourage you. With some distro's of linux it is possible, but it may not be easy.

**Edited to remove irrelevant PAE information.**

---

### Post by fantab on 2013-03-14
Welcome!

How did you BURN Lubuntu on the install media?

Lets first rule out a bad download and/or a bad burn lubuntu on CD/USB. Do a [MD5SUM CHECK]("https://help.ubuntu.com/community/HowToMD5SUM") on your downloaded lubuntu.iso image. If its not OK then re-download Lubuntu ([torrent]("https://help.ubuntu.com/community/Lubuntu/GetLubuntu") download is recommended). 
Then [Burn to CD/DVD]("https://help.ubuntu.com/community/BurningIsoHowto") or [Burn to USB]("https://help.ubuntu.com/community/Installation/FromUSBStick"). Use [Unetbootin]("http://unetbootin.sourceforge.net/") if your are burning the lubuntu image on USB.

Edit: If all the above checks are fine and if you still have problems then as suggested in previous post use the [Lubuntu Alternate Installer]("https://help.ubuntu.com/community/Lubuntu/Alternate_ISO") and read the [How To]("https://help.ubuntu.com/community/Lubuntu/Documentation/AlternateInstall").

---

### Post by mastablasta on 2013-03-14
> **billbobagwell said:**
> hey, i am new to ubuntu. I decided to finally try to escape the windows world, so i searched around and thought lubuntu looked pretty interesting. Never using anything besides windows i decided to try lubuntu on an ol' cheapie. so here's my problem. i have a toshiba satellite 1800-s203 with 800mhz intel celeron, 256mb ram, 40 hd and a 8mb Trident Microsystems Cyber-blade AI1 video chip. When i try to install it will begin, blue screen with Lubuntu 12.10 loading, then after about 5mins it goes black with lubuntu 12.10 still loading and finally it just goes black. I've tried nomodeset but still nothing:( please help!




1. use 12.04.
2. you wont' be able to use graphical installer with 256 ram. it will crash (which is probably what happened)
3. as suggested use alternate installer or minimal iso (i.e. network install...).

here is a nice how to with pics: [http://www.psychocats.net/ubuntu/minimal](http://www.psychocats.net/ubuntu/minimal)
link to mini iso.: [https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)


Another option is to use a different os that will be friendlier to your system. i can suggest Chrunchbang (very easy to install for us newbies) and AntiX (easy on resources, looks like win95 with modern progs)). both are debian based (well antix is mepis based which is debian based) with large repositories of applicaitons and such.
 
if all of these are too small have a look at puppy linux (independent development) or slitaz which are made for old mashcines.

---

### Post by mörgæs on 2013-03-14
I assume we are dealing with this CPU:
[http://ark.intel.com/products/27197/Intel-Celeron-Processor-800-MHz-128K-Cache-100-MHz-FSB](http://ark.intel.com/products/27197/Intel-Celeron-Processor-800-MHz-128K-Cache-100-MHz-FSB)

In that case PAE is not a problem. Please don't bring the PAE ghost into each and every discussion regarding old hardware.

The problem here is lack of RAM. You will not have a usable system unless you give it at least 500 MB (and even then it will be slow).

---

### Post by sudodus on 2013-03-14
> **billbobagwell said:**
> hey, i am new to ubuntu. I decided to finally try to escape the windows world, so i searched around and thought lubuntu looked pretty interesting. Never using anything besides windows i decided to try lubuntu on an ol' cheapie. so here's my problem.  i have a toshiba satellite 1800-s203 with 800mhz intel celeron, 256mb ram, 40 hd and a 8mb Trident Microsystems Cyber-blade AI1 video chip. When i try to install it will begin, blue screen with Lubuntu 12.10 loading, then after about 5mins it goes black with lubuntu 12.10 still loading and finally it just goes black. I've tried nomodeset but still nothing:( please help!

P.S. I have a feeling it may have something to do with the graphics chip being how its kinda an out there old card

okay now it went to the black loading screen and said *starting *starting *stopped and then nothing again

I agree with the other people, that you need more memory to get a working system, that can browse the internet in a reasonably convenient way.

***But if you want to play with linux on this machine***, just to learn, it will be possible to install Lubuntu from the alternate CD, and to run it. My Lubuntu 12.04 uses 121 MB RAM idling (after log in), only half of your 256 GB of RAM. But I suggest that you download the 12.10 alternate iso file, because Lubuntu 12.04 end of life is in October this year.

It is also possible to run any of the tiny linux distros suggested: Chrunchbang, AntiX, puppy linux, slitaz. I can add DSL (damn small linux) to that list.

---

### Post by mastablasta on 2013-03-14
Then again RAspberry pi has a CPU like 250 Mhz pentium i believe and first version had 256MB ram. wasn't anything fast but it did the job realively well. i htink the GPu they use is sort of stornger than yours.

it much depends on applicaitons and what you plan to do with the maschines. 

i use chrunchbang XFCE on the old 256MB maschine. it is based on current Debian stable 6.it uses about 80 MB ram on idle according to conky. might be a bit more. anyway can watch movies, browse the web... but the graphcis chip is a bit stronger and CPU is 1.2Ghz.

---

### Post by fantab on 2013-03-14
I agree with mastablasta, [CRUNCHBANG]("http://crunchbang.org/") is an excellent distro when it comes to a minimal working OS with GUI, for those new to Linux and for those with low spec machines.

---

### Post by billbobagwell on 2013-03-14
thanks for all the help and suggestions, but i'd rather try this on a more friendly computer... The dinosaur i'm working with now isn't worth all the trial and error. I'm only about a year into working with computers and most of the stuff i've done is more hardware and very little software. I really appreciate all the help! But i was thinking about trying some kind of Buntu on a compaq presario sr2011wm desktop with an Intel Celeron D 3.2mhz, 2gb ram, ATI Radeon Xpress200. Think i would run into any problems there and what OS would be best to try on this? Thanks again!

---

### Post by ManamiVixen on 2013-03-14
The Compaq will work, just watch out for the ATI. It could be trouble. As for OS, its good enough to run anything, even if some like Ubuntu with Unity might be slow.

As for the First laptop, Puppy is the best option. Puppy Linux is small, fast, easy to use, and requires little Linux knowledge to use.

---

### Post by billbobagwell on 2013-03-14
> **ManamiVixen said:**
> The Compaq will work, just watch out for the ATI. It could be trouble. As for OS, its good enough to run anything, even if some like Ubuntu with Unity might be slow.

As for the First laptop, Puppy is the best option. Puppy Linux is small, fast, easy to use, and requires little Linux knowledge to use.


Thanks! I'll give Puppy a try on the toshiba and ask for the compaq, i'll just read up and see what looks best.

---

### Post by billbobagwell on 2013-03-14
which puppy should i use? There's like Slacko, Precise, Lucid etc.

---

### Post by ManamiVixen on 2013-03-14
Precise Puppy should be good. It's compatible with packages from Ubuntu 12.04, but unlike 12.04 the entire OS is just 166MB in size and can load itself in it's entirety into the Toshiba's 256MB ram and never need to access the hard disk ever. And when you are done on the PC and shutting it down, it will ask were you would like to save everything you have done to the OS durring the current session to say a place on the hard disk. Did I also mention all codecs, flash, and java are installed by default. :) At least they were the last time I used Puppy last year.

---

### Post by billbobagwell on 2013-03-14
Kewl:guitar: Downloading it now! I'll update on how it goes.

---

### Post by billbobagwell on 2013-03-15
well still end up having a black screen. i read up a little and ubuntu doesn't support trident graphics with legacy chipsets so i'll just leave the ol toshiba runnin XP... thanks tho:)

---

### Post by mörgæs on 2013-03-15
> **ManamiVixen said:**
> The Compaq will work, just watch out for the ATI. It could be trouble.

The trouble refers to the fact that no closed-source drivers are available. The card will run fine with open-source drivers for normal work, but you will not be able to run 3D games and similar heavy graphics.

---

### Post by mastablasta on 2013-03-15
> **billbobagwell said:**
> well still end up having a black screen. i read up a little and ubuntu doesn't support trident graphics with legacy chipsets so i'll just leave the ol toshiba runnin XP... thanks tho:)


did you try any of the boot options?
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)


you just might need to do some manual configuration. 

[http://ubuntuforums.org/showthread.php?t=1199881](http://ubuntuforums.org/showthread.php?t=1199881)
[http://ubuntuforums.org/showthread.php?t=763964](http://ubuntuforums.org/showthread.php?t=763964)

as long as the driver is still in kernel the only things that needs to be figured out is how to boot the OS and configure it in 12.04. 

are you saying that when you boot you don't even get to see grub? i mean you should be able to get to at least some basic functionality GUI or at least some text output on screen.


you might also give DSL (damn small linux) a shot if you can't get it to run with Ubutnu. it uses quite old kernel. this is not good for new maschines but a blessing for the old hardware.

---

### Post by 3rdalbum on 2013-03-15
> **ManamiVixen said:**
> The Compaq will work, just watch out for the ATI. It could be trouble.

My father has a machine very similar to that, except with an AMD CPU. The Xpress 200 works, but unacceptably slowly on 12.10 due to the low 3D support and Unity's insistence on semi-transparency.

It's possible to turn off the semi-transparency, but Unity's still a bit slow.

If you use Ubuntu 12.04 instead, you can use a 2D version of Unity. Or, alternatively, you can install 12.10 and then change desktop environment.

---

### Post by chrisod on 2013-03-15
I'm running Puppy Slacko on an old pentium M laptop and it works just fine. Give it a shot.

---

