---
title: "Multi boot MBR mess"
date: 2008-11-23
forum: New to Ubuntu
---

### Post by LvxDemos on 2008-11-23
I have managed to mess up my MBR. I am triple booting Win XP, Win Server 2008 and Ubuntu 8.10. I have managed to recover GRUB loader via the live cd following a howto on this forums. However, I'm stumped when it gets to fixing the Windows Loader - it refuses to recognise any Windows. I am attaching a screenshot of my partition configuration (because I don't know the code to list it :( ): [IMG]http://i281.photobucket.com/albums/kk211/Fuddha/Gparted02.jpg[/IMG]

sda1 is WinXP
sda2 is WinServ2008
sda3 is a shared NTFS partition

1) How can I fix the Windows loader from Ubuntu?
2) Where should the boot flag be?
3) Why did Ubuntu installer insist that I leave 5MB of unallocated space between sda2 and sda3 partitions?

Thanks!

---

### Post by Dedoimedo on 2008-11-23
Hello,
You can boot from Windows CD, fix MBR.
Then you can boot from, let's say, Super Grub Disk, and fix GRUB.
It's simple and should work well.
Dedoimedo

---

### Post by Gone fishing on 2008-11-23
I place grub on the linux partition and use GAG as a boot loader. I thoroughly recommend it - its easy, has useful features and will have you booting your Oses in minutes [http://gag.sourceforge.net/](http://gag.sourceforge.net/)

---

### Post by LvxDemos on 2008-11-23
For some reason the Win Server 2008 install CD won't recognize my hard disk at all and I can't repair it like that. Also, it specifically says that it can't repair any Windows versions earlier that Vista. Should I boot up from XP cd and repair MBR trough the console and then hope that Server install CD will recognize my hard disk after that?
I mean, the OSes are already set up and configured the way I like, I wouldn't want to find myself in a tight spot where I must reinstall and reconfigure them again.

edit: Gone fishing has ninjad a post while I was typing mine. I'll try out the GAG.

---

### Post by caljohnsmith on 2008-11-23
If you successfully recovered Grub and get the Grub menu on start up, I don't think you want to reinstall a Windows MBR or you won't be able to boot anything but your Windows install on sda1. All you should need to do is add an entry to boot Windows in your Grub's menu.lst. While you are in Ubuntu, how about opening a terminal (Applications > Accessories > Terminal) and do:
```
gksudo gedit /boot/grub/menu.lst
```
And then at the bottom, add the following:
```
title Windows XP
root (hd0,0)
chainloader +1
```
Reboot, and let me know what happens when you boot Windows from Grub, and we can work from there. :)

---

### Post by Rabindranath on 2008-11-23
You can use EasyBCD. I once triple booted Vista, XP and ubuntu with it...

---

### Post by LvxDemos on 2008-11-23
> **Rabindranath said:**
> You can use EasyBCD. I once triple booted Vista, XP and ubuntu with it...

Yeah, EasyBCD caused all this trouble in the first place. Apparently it was built with Vista in mind but not Server 2008. In theory it should work as the Windows Loader is the same. However it does not. Or I am a nooblet. Or both...

> **Gone fishing said:**
> I place grub on the linux partition and use GAG as a boot loader. I thoroughly recommend it - its easy, has useful features and will have you booting your Oses in minutes [http://gag.sourceforge.net/](http://gag.sourceforge.net/)
I didn't see any MBR fixing in the options nor in the documentation. It seems to me that it is a mere GUI loader. I installed it though and it broke my GRUB so I had to rebuild from live cd. Again.
However, I'm in a hurry here so I could've easily missed it though.

> **caljohnsmith said:**
> If you successfully recovered Grub and get the Grub menu on start up, I don't think you want to reinstall a Windows MBR or you won't be able to boot anything but your Windows install on sda1. All you should need to do is add an entry to boot Windows in your Grub's menu.lst. While you are in Ubuntu, how about opening a terminal (Applications > Accessories > Terminal) and do:
```
gksudo gedit /boot/grub/menu.lst
```
And then at the bottom, add the following:
```
title Windows XP
root (hd0,0)
chainloader +1
```
Reboot, and let me know what happens when you boot Windows from Grub, and we can work from there. :)

Here is what's currently in the file:
```

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows Vista/Longhorn (loader)
root		(hd0,1)
savedefault
makeactive
chainloader	+1

```

The Windows loader is there and no other entries but usual ones (kernel, kernel in recovery mode and memtest), so the problem isn't in GRUB. It seems that Windows loader itself is broken. Can I fix this from Ubuntu? I am reluctant to fix MBR from Windows install CDs (I am triple booting here afterall).

edit: Just noticed that it says that the root for Windows loader is on hd0,1. Should it be 0,0?

---

### Post by caljohnsmith on 2008-11-23
> **LvxDemos said:**
> 
edit: Just noticed that it says that the root for Windows loader is on hd0,1. Should it be 0,0?
Yes, you said XP was on sda1, so the Grub entry should be (hd0,0) and not (hd0,1). :)

---

### Post by LvxDemos on 2008-11-23
Solved it.

First I booted from a XP cd and repaired it's boot.ini in the recovery console. That killed Grub and Server 2008 but it allowed me to boot to XP. After that, I booted from the Server 2008 cd and reformated its partition and reinstalled it. Then I (ironically) installed EasyBCD in Server 2008 and added an entry for Windows XP in the Windows Longhorn loader with it. After that, I coul boot in both XP and Server 2008. That left me with fixing Grub only. I booted a live session from Ubuntu cd and fixed Grub. I only lost the Server 2008 partition, but the damage is not so big as I didn't have anything vital on it.

In the end I can say I learned a valuable lesson today:
[COLOR="Red"][SIZE="5"]NEVER EVER MESS WITH YOUR MBR IF YOU DON'T ABSOLUTELY HAVE TO![/SIZE][/COLOR]
and
IF YOU DO MESS UP YOUR MBR, TAKE IT SLOW AND DON'T PANIC!
:biggrin:



Thank you all for the help!

---

