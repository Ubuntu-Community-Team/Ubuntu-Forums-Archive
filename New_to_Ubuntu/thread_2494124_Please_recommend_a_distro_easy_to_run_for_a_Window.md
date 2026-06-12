---
title: "Please recommend a distro easy to run for a Windows user."
date: 2024-01-05
forum: New to Ubuntu
---

### Post by kuen2 on 2024-01-05
My PC.
Acer desktop T3 715
Windows 10 Home 64b. 22H2
SSD 128GB plus (D:) 3.5" SATA3 1.0TB  & an emplty 3.5" SATA3 1.0TB
CPU Intel Core i5-6400  
DDR4-SDRAM 16B 2133MHzDDR4-SDRAM
GPU NVIDIA GeForce GTX 950

I wish to run a Linux Distro on the above machine.

A friend of mine uses Linux Mint Xfce.  I played with his computer many times, and found 1. its desktop is similar to that of Windows, 2. firefox and Google Chrome are installed and can be used normally, and 3. too slow at booting, around 2 minutes from power on to use of Chrome.

Information on Google Search recommends KDE Ubuntu, and says that KDE desktop is much more like that of Winows.   I have no knowledge of Ubuntu and KDE.  So, come here for advices.

In 2007 or 2008,  I tried to learn Ubuntu.  Gave it up because it was too difficult for me to run, especially Gimp.

Is Ubuntu still hard to use, one command for one action?
Is KDE Ubuntu providing a desktop as or similar as that of Windows?

Thank you.

---

### Post by QIII on 2024-01-05
You have written about Kubuntu -- and the interesting part about KDE is that for a long time it seemed that KDE and Microsoft were in a war to one-up each other and produce desktops that were very similar.  
Your machine is perfectly capable of running Kubuntu.

Kubuntu might be very familiar to you.  I use Kubuntu because it is very customizable, but in a default configuration it would probably be relatively familiar.  However, you should bear in mind that Linux is substantially different than Windows.  Whatever distribution and desktop you choose, you will have a steep learning curve.  Linux is only "difficult" if you cling to Windows-isms and are not willing to learn something new.

With regard to being "slow", that is an illusion based on the fact that Windows uses some trickery to appear to boot faster.  It relies on a hybrid form of hibernation and bypasses POST (Power On Self Test), which is actually dangerous.

I started playing with computers back in the day when Unix was pretty much all there was -- before Windows even existed.  So Linux was familiar and comfortable to me.  Learning Windows frustrated me when it first appeared.  Still, I eventually went on to own a software development company that specialized in Windows applications.

GIMP is definitely different from any Windows programs.  You will have to be willing to learn.

"Hard" is subjective.  German might be "hard" to learn for a native English speaker, but I was able to learn it.  One of my degrees is in German Literature.  Learning Linux is the same as learning a new spoken language.  It just takes time.

---

### Post by Dennis N on 2024-01-05
The distro that's targeted to Windows users who want to switch to Linux is Zorin. It's based on Ubuntu. The default appearance will be familiar with a start menu.

---

### Post by guiverc on 2024-01-06
> **kuen2 said:**
> 3. too slow at booting, around 2 minutes from power on to use of Chrome.


Just a comment.

If you're comparing a GNU/Linux system which does a full *cold* boot, to a windows system which has *fastboot* enabled, you're comparing two *rather *different things.

Windows *fastboot* is a restore of a *hibernate* file, that is created after upgrades are applied to the windows system. It's not a *cold boot*, which is what GNU/Linux systems do by default.

If you're *slow *isn't because of a *faulty* comparison such as this, look at what *autostarts*, as you can make *boot* faster by having less *autostart*, and have those *starts* only occur the first time something using them is run.

People didn't like *windows 2000* because it took *double-digit* minutes to boot, as it *autostarted* everything, making operation of the OS faster after it eventually booted, but the boot very slow. eg. if you'd used 5 printers some time in the distant past on a machine, windows 2000 was slow to boot as it prepared to print on all those printers, even if none of them were attached (*or hadn't been used in the prior two years either*). You can control most of this, just as you could in the windows world (*the defaults just differ a little; just as XP & later did away with decision decisions included in windows 2000 in this example*).

---

### Post by notentirlynewb on 2024-01-06
I'm a newbie so please take my opinion with a large carton of salt..but I've been using Ubuntu mate on my older desktop and enjoy it very much..but that's a newbie opinion and lots of salt lol

---

### Post by ian-weisser on 2024-01-06
> **kuen2 said:**
> Is Ubuntu still hard to use, one command for one action?

Ubuntu has never been hard to use *for most folks*. 
We don't know you. We don't know what you consider a dealbreaker. Only you know that.


> **kuen2 said:**
> Is KDE Ubuntu providing a desktop as or similar as that of Windows?

Yes. And KDE also did that 15 years ago.
Ubuntu/Kubuntu is NOT a drop-in replacement for Windows, and has never promised to be.
It's different, and you must be willing to embrace those differences.

---

### Post by oldfred on 2024-01-06
Any Linux system that takes two minutes to boot is mis-configured.
 Does not include UEFI/BIOS & grub. I change grub from 10 to 3 sec. Do not have fast boot on.
I can shutdown & reboot in about 20 sec total unless I forget to unmount an external drive & then it has to time out.
```
[FONT=monospace][COLOR=#54ff54]**fred@Z170-jammy**[/COLOR][COLOR=#000000]:[/COLOR][COLOR=#5454ff]**~**[/COLOR][COLOR=#000000]$ systemd-analyze [/COLOR]
Startup finished in 4.100s (kernel) + 6.211s (userspace) = 10.312s  
graphical.target reached after 6.176s in userspace
[/FONT]
```

I now have NVMe type SSD, before had M.2 SSD SATA type but NVMe is only a bit faster.
This is on my 2017 build with z170 motherboard & [FONT=monospace][COLOR=#000000]Intel Core i5-6500 .

some threads with settings to improve boot.
[https://ubuntuforums.org/showthread.php?t=2450783](https://ubuntuforums.org/showthread.php?t=2450783)
[https://ubuntuforums.org/showthread.php?t=2436900&p=13932499#post13932499](https://ubuntuforums.org/showthread.php?t=2436900&p=13932499#post13932499)
[https://ubuntuforums.org/showthread.php?t=2417453](https://ubuntuforums.org/showthread.php?t=2417453) & 
[https://ubuntuforums.org/showthread.php?t=2417453&p=13857392#post13857392](https://ubuntuforums.org/showthread.php?t=2417453&p=13857392#post13857392) & 

[/COLOR]
[/FONT]

---

### Post by MAFoElffen on 2024-01-07
+1 ---
```

mafoelffen@Mikes-ThinkPad-T520:~$ systemd-analyze
Startup finished in 7.908s (kernel) + 12.049s (userspace) = 19.957s 
graphical.target reached after 12.012s in userspace

```
That's on a Lenovo ThinkPad T520. It's almost 13 years old. The config has a lot going one, just because it is a very complex filesystem, and still boots cold in 19 seconds.

When I installed Linux for my customers, many were new users, who it was easy for them. Why? Because they learned what they needed to do to do what they wanted to, or needed to do... Without having to relearn how to do something. To them, it was just what they did.

I support Windows, Unix and Linux. Linux is my day-to-day driver.

---

### Post by him610 on 2024-01-07
My machines all run Xubuntu 22.04.3. The specs of my oldest ....
```
hugh@kabini:~$ screenfetch && systemd-analyze
                          ./+o+-       hugh@kabini
                  yyyyy- -yyyyyy+      OS: Ubuntu 22.04 jammy
               ://+//////-yyyyyyo      Kernel: x86_64 Linux 6.2.0-39-generic
           .++ .:/++++++/-.+sss/`      Uptime: 1d 15h 28m
         .:++o:  /++++++++/:--:/-      Packages: 2006
        o:+o+:++.`..```.-/oo+++++/     Shell: bash 5.1.16
       .:+o:+o/.          `+sssoo+/    Disk: 221G / 2.8T (9%)
  .++/+:+oo+o:`             /sssooo.   CPU: AMD Athlon 5350 APU with Radeon R3 @ 4x 2.05GHz
 /+++//+:`oo+o               /::--:.   GPU: Advanced Micro Devices, Inc. [AMD/ATI] Kabini [Radeon HD 8400 / R3 Series]
 \+/+o+++`o++o               ++////.   RAM: 1749MiB / 7364MiB
  .++.o+++oo+:`             /dddhhh.  
       .+.o+oo:.          `oddhhhh+   
        \+.++o+o``-````.:ohdhhhhh+    
         `:o+++ `ohhhhhhhhyo++os:     
           .o:`.syhhhhhhh/.oo++o`     
               /osyyyyyyo++ooo+++/    
                   ````` +oo+++o\:    
                          `oo++.      
Startup finished in 4.665s (kernel) + 19.433s (userspace) = 24.099s 
graphical.target reached after 19.410s in userspace


```

---

### Post by ActionParsnip on 2024-01-08
+1 for KDE

It'll give you a familiar feel (bar at the bottom, menu in the bottom left corner and so on)

---

