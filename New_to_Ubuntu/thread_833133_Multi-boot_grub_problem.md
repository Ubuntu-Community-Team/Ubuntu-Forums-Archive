---
title: "Multi-boot grub problem"
date: 2008-06-18
forum: New to Ubuntu
---

### Post by wolfestine on 2008-06-18
I have been using Ubuntu (gutsy 64) for a while now n have been solving my problems going through other threads. But i just can't find one for my present problem and it has bugged me enough to considering going back to windows. I need help :confused:

I was a windows XP user n later on switched to Vista. Next I installed Ubuntu, n since I was a windows user, I asked in one of those windows forums about how to set up a multi-boot. I was advised to use EasyBCD, n so i did use it. So things were a little messed up because of the complicated boot procedure (Vista's BCD followed by the GRUB) so I put a copy of the grub on my flash drive to simplify the boot procedure. Now I have installed FC9 KDE 64 and I installed it's grub on it's own drive (rather than the MBR, like i did for my ubuntu) but I can't add it to either easy BCD or the GRUB. What's more is that I can't boot the ubuntu using the original grub or the one in the pen-drive. Strangely my XP's ntoskrnl.exe got corrupt too n replacing the old one doesn't solve the problem. In the GRUB which loads after the Vista BCD, it does give me a command line, using which i can boot the FC9 but not Ubuntu. I intend to install Ubuntu64, Kubuntu64 (Hardy) along with FC9 GNOME64, Linux Mint, PCLinuxOS n the upcoming Open Suse 11 along with my current list of OS's (XP, Vista, FC9KDE, Ubuntu(gutsy)). Could somebody please help me set em up? Where should I start from. Oh n they are all on the same hard-disk. I am forced to use vista n i hate it. Please help. :(

---

### Post by alexandremrj on 2008-06-18
I would recomend Super Grub disk

Take a look at this page of the wiki:
[http://www.supergrubdisk.org/wiki/Multi_Distribution_Boot_Howto](http://www.supergrubdisk.org/wiki/Multi_Distribution_Boot_Howto)

See if you can understand it and if you need any help just ask here to continue the thread.

---

### Post by yragrelluf on 2008-06-18
Why do you need so many OS? I think it would be easiest to reinstall an OS of your choice "id go with hardy" and then install other OS, and use the manual partition edit when installing them. That would also solve your biggest problem of having vista on your computer.:lolflag:

---

### Post by wolfestine on 2008-06-18
@alexandremrj
Thank you for pointing that 'how to' out. I had already tried out the commands in the GRUB command line, but hadn't added em to the menu.lst file. But I can't get my ubuntu to boot up.
Also I was using *root* instead of *rootnoverify* command, but since *root* was working fine earlier, I don't think that should be too much of a problem. Instead of seeing the screen where the kernel is activated, I now see the grub commandline where I enter 

root (hd0,8)   /   rootnoverify (hd0,8)
chainloader +1
boot

n i end up at the GRUB commandline again with all previous commands cleared from the console. I am certain that this is the harddrive n partition number are okay, since I used the geometry command to verify that.


@yragrelluf
Ah well let's see, I didn't need Ubuntu either, my system was running fine on XP :tongue: too. But somebody told me Ubuntu that ubuntu rocked :guitar: n I tried it out n liked it. Now I intend to try out atleast a dozen distributions (those that people I know recommend) before I can say confidently that Ubuntu is THE BEST. :lolflag:

---

### Post by alexandremrj on 2008-06-18
Wolfestine,

you can download SuperGrubDisk from here [http://www.supergrubdisk.org/](http://www.supergrubdisk.org/) and install it to USB, disk or CD-Rom to repair your grub menu. Check the page for Grub for windows also

---

### Post by tjwoosta on 2008-06-18
dude whats up with all the complication?

> I was advised to use EasyBCD
(this is your problem)

it doesnt have to be so complicated

first you have the original windows installation with the windows bootloader

so without doing anything to the MBR and without installing EasyBCD just pop in the live cd and install ubuntu like normal

when it asks how you would like to install grub, **install it to the MBR**

this will replace the vista bootloader with grub 

grub will boot vista or Ubuntu or any distro no problem (it jsut gives you a list of installed OS's)


so basically you dug yourself into a hole by not installing to MBR

---

### Post by bodhi.zazen on 2008-06-18
[How to Multi-boot (Maintain more then 2 OS) - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=724817")

To multiboot windows with grub you need to hide and sometimes map.

[http://users.bigpond.net.au/hermanzone/p15.htm#Grub_and_MultiWindows_](http://users.bigpond.net.au/hermanzone/p15.htm#Grub_and_MultiWindows_)

You can also look at Supergrub

---

### Post by wolfestine on 2008-06-19
Thank you *bodhi.zazen* and *alexandremrj*. That was some insightful reading. 
Super Grub does seem like a nifty tool, I'll try it out on my pendrive first, n then if I am comfortable with it, I'll hand my MBR to it.

I improvised, n added the fedora to the vista BCD, and got it working.

(@ tjwoosta : Am I making a mistake here? If I let grub/supergrub handle my MBR u sure I wouldn't have any problems with multi windows installations? What can I do right now to switch to grub and not mess it all up, cause I can't boot windows from the grub manually.)


Then I fooled around with the grub in my pendrive and got it working too. But I can't get the one on my hard-disk working. 

This is the menu.lst entry on my hdd

```
title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,8)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=1447fdb5-9b47-408b-81eb-d75b17b71017 ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet
```

And this is the one on my pen-drive

```
title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd1,8)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=1447fdb5-9b47-408b-81eb-d75b17b71017 ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet
```

they are exactly the same except the hard-disk number, which changes automatically when I plug-in my pendrive. So I guess they are both the same. I can't even get the the grub on my hdd to boot ubuntu manually. What can I do about it. Also how should I go about the other installations??? Should I install their respective grubs on their own partition or should I let each installation handle my MBR as I proceed. Or should I make a boot partition to handle everything? Still confused

Wolfestine.

---

### Post by bumanie on 2008-06-19
You may find this an interesting read. It has almost everything you need to know about grub and multi-booting. [http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)

---

### Post by tjwoosta on 2008-06-19
> Am I making a mistake here? If I let grub/supergrub handle my MBR u sure I wouldn't have any problems with multi windows installations? What can I do right now to switch to grub and not mess it all up, cause I can't boot windows from the grub manually.)


go to the first link that bodhi.zazen posted and read number 1, it tells you about how to hide and map, in order to boot multiple windows installations (ive never booted multiple windows before so i cant really help you much)

sry but i also cant seem to find any literature about moving grub from a boot sector back to the MBR (only from MBR to a boot sector)

---

### Post by Duck2006 on 2008-06-19
[http://apcmag.com/the_definitive_dualbooting_guide_linux_vista_and_xp_stepbystep.htm](http://apcmag.com/the_definitive_dualbooting_guide_linux_vista_and_xp_stepbystep.htm)

---

