---
title: "Dual booting Ubuntu on Pentium 4"
date: 2011-11-24
forum: New to Ubuntu
---

### Post by gatgat23 on 2011-11-24
I have a problem when dual-booting Ubuntu 11.10 with Windows 7 on Pentium 4. I used Wubi and Ubuntu run flawlessly. Then when I boot up my Windows 7, BSOD appears. It says "Physical Memory dumping". With the file names "ewnetusb.sys". 

Here's what I did:
1. Installed Wubi.
2. Finished installing Ubuntu.
3. Used Update Manager to update.
4. Installed some additional drivers for my Video card.
5. Restart.
6. Run Ubuntu again to make sure that the updates are installed.
7. Restart.
8. Boot up Windows 7.
9. BSOD.

I, now, using Windows XP. I want to try with Windows XP, but I'm afraid that it might also happen, so I post here first.

BTW, here's the specs of my PC:
Processor: Intel Pentium 4 2.66Ghz
RAM: 1GB DDR4
Video Card: nVidia GeForce 5500 FX with 256 RAM.

Thanks for all your replies. :)

---

### Post by lolpenguin on 2011-11-24
Please post the output of your BSoD.

---

### Post by gatgat23 on 2011-11-24
> **lolpenguin said:**
> Please post the output of your BSoD.
I can't. As I already formatted to Windows XP because of that BSOD. I want to install Wubi again in my Windows XP, but I'm afraid it might happen again. Help.

---

### Post by mastablasta on 2011-11-24
> **gatgat23 said:**
> 3. Used Update Manager to update.

 
this step is what caused the problem. wubi is ment for testing the OS. to use it on more permanent basis (and this is not advised) you need to set it up propperly. 
 
have a look at this thread for extensive troubleshooting and help on wubi: [http://ubuntuforums.org/showthread.php?t=1639198](http://ubuntuforums.org/showthread.php?t=1639198)
 
likely your boot record got messed up due to updates. hope you can solve this.

---

### Post by lolpenguin on 2011-11-24
> **mastablasta said:**
> this step is what caused the problem. wubi is ment for testing the OS. to use it on more permanent basis (and this is not advised) you need to set it up propperly. 
 
have a look at this thread for extensive troubleshooting and help on wubi: [http://ubuntuforums.org/showthread.php?t=1639198](http://ubuntuforums.org/showthread.php?t=1639198)
 
likely your boot record got messed up due to updates. hope you can solve this.

Actually, I am a Wubi user and have not experienced any problems, having upgraded from Natty to Oneiric. I do not know why people think that Wubi is for testing only. But updating within the install should not mess up the MBR of the Windows partition, and if it does, Windows wouldn't even boot, so no BSoDs would occur.
When I buy a shiny SSD however, I will install a clean version of Oneiric onto it.

---

### Post by gatgat23 on 2011-11-24
Ok. I found that there's a problem in my Windows XP now. I think it's time for me to test installing Wubi again, but with XP, not Win7. I'll post if I can't still boot. And post the BSOD. (If it appears!) :)

---

### Post by gatgat23 on 2011-11-24
> **gatgat23 said:**
> Ok. I found that there's a problem in my Windows XP now. I think it's time for me to test installing Wubi again, but with XP, not Win7. I'll post if I can't still boot. And post the BSOD. (If it appears!) :)
Hey, it works. But with XP. Not Win7. I guess Pentium 4 is really for XP? :confused:

---

### Post by LinuxFan999 on 2011-11-24
> **gatgat23 said:**
> Hey, it works. But with XP. Not Win7. I guess Pentium 4 is really for XP? :confused:
That computer is a bit to old to run Windows 7, especially since it only as 1GB of RAM. If this computer isn't your main computer, you could replace Windows with Ubuntu and forget about Wubi.

---

### Post by gatgat23 on 2011-11-24
> **LinuxFan999 said:**
> That computer is a bit to old to run Windows 7, especially since it only as 1GB of RAM. If this computer isn't your main computer, you could replace Windows with Ubuntu and forget about Wubi.
I want to, but I can't. I have a scanner and I can't get it to work with Ubuntu. Even with SANE.

---

