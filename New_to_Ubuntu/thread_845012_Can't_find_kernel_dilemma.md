---
title: "Can't find kernel dilemma"
date: 2008-06-30
forum: New to Ubuntu
---

### Post by Midgetprawn on 2008-06-30
I am dual booting Hardy with XP and following a reinstall on a separate partition I am unable to reboot Ubuntu. AHA thinks I, I can use GAG or SGD to reinstall GRUB. However when I try to link to the Grub folder and reboot I get a message something like "SLKD.... unable to fond kernel...."

Have I over written something by reinstalling XP. 
I tried a reinstall but it wanted to open a separate partition.
I don't want to mess up my current files and settings

---

### Post by ajgreeny on 2008-06-30
> I am dual booting Hardy with XP and following a reinstall on a separate partition I am unable to reboot Ubuntu.A reinstall of what, windows or ubuntu?
Boot up the live ubuntu CD and you will be able to see if your installed ubuntu is still there easily enough by mounting the partitions using nautilus (double clicking on them).  Assuming it is still there then use the live CD to reinstall grub as follows:-
Boot into the ubuntu live CD
open a terminal and run :
    sudo grub
This gets you to a simple grub command line.
Then:
    find /boot/grub/stage1
This will tell you where your /boot/grub/stage1 is which is needed to boot ubuntu. Replace the question marks in the following command with the output of the this last command :
    root (hd?,?)
[like : root (hdo,1) ,probably]
then:
    setup (hd0)
This is where your windows partition and MBR normally is, but if you want grub on another disk, use hd1, etc as appropriate. It's much easier to use the windows MBR and then just change the default boot system later if others in the family demand windows boots by default.
Then:
    quit
Finally reboot, and hopefully you will now have a working grub bootloader.

I hope that helps.

---

### Post by Midgetprawn on 2008-06-30
Thanks but doesn't GAG and SuperGrub Disc look for the Grub file?

Sorry it was XP I reinstalled.

Yes Ubuntu is still in it's partition and intact as I ran the live disc.

I am AFK for my Ubuntu computer at the momen but I will try this suggestion later.

Thanks again

---

