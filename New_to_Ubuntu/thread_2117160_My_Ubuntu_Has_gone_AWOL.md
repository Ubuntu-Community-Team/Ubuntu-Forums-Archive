---
title: "My Ubuntu Has gone AWOL"
date: 2013-02-17
forum: New to Ubuntu
---

### Post by sunnycreatives on 2013-02-17
So....I went to the Ubuntu site and tried to install Ubuntu.

Got a message up saying that I needed to reboot to complete the installation ...so rebooted, Windows started up and I can't see any sign of the Ubuntu that should have been installed.

What did I do wrong???

I am using a PC with Windows XP

To see if I had messed up, I re-installed Ubuntu after uninstalling the one I had installed previously, but still no Ubuntu 

Below is the reply I received after posting this problem on another forum

"If you have successfully installed Ubuntu then when you reboot you should get a choice of which OS you wish to use, Ubuntu or Windows...... use the up/down arrows to select.
If you missed seeing that page then your puter might have gone straight to Windows by Default."

I didn't get any choice of OS when rebooting as Windows started up automatically.

---

### Post by Bashing-om on 2013-02-17
sunnycreatives; Hi ! Welcome to the forum.

Should have installed with no problem IF:
You made provisions with windows to make up some "unallocated" space on the disk for ubuntu OR chose to "install ubuntu along side of" other operating system.

Lets see what is on the hard drive at this time.
Boot up with the install liveCD -> try ubuntu -> desktop:
At the desktop (12.04 version) left side is the launcher, top icon activates the "dash" -> enter into dash's search box the term "GParted" -> icon below dash -> click on the GParted icon to activate GParted (ubuntu's partition editor).

Please post a screen shot of what is shown.
[INDENT][INDENT]just try'n to help

[/INDENT][/INDENT]

---

### Post by baseballa51 on 2013-02-17
Are you doing a dual boot from one hard drive? or is there a windows hard drive and an ubuntu hard drive?

How did you partition your (single) hard drive for a dual boot? I have always set up partitions manually before either installation, as opposed to "resizing partitions" etc.. (I always install Windows First for a dual boot). After installing windows on it's designated NTFS partition then I boot from a live CD/usb and specify partitions manually. My ubuntu partition settings are as follows:

Check Primary partition, mount point is "/", and file system is "ext4". "swap" partition is good to have for memory overflow and is recommended a minimum of 4gb.

It is possible that Grub has defaulted to Windows (improbable) but I've seen it happen when the ubuntu partition doesn't have the correct boot settings or mount point. Is there a lag time after the motherboard bios is done posting where you get a blank or black screen for about 10 seconds and then you see Windows booting? Grub may have loaded but is in a resolution which your monitor does not recognize. If this is the case, during that "lag time" try to arrow down or up to see if your computer will boot into ubuntu or in safe graphics mode --just to see if grub is actually loaded.

---

### Post by sunnycreatives on 2013-02-18
Oh dear...I have no idea what any of the replies mean.

I didn't use a start up disc just downloaded for free from the Ubuntu site.

Also I have no clue how to partition a hard drive.

I am wondering since my PC is nearly 7 years old and getting extremely unreliable if my best bet was to wait until I can have another PC built with Ubuntu included:lolflag:

---

### Post by Impavidus on 2013-02-18
Sounds like you did a wubi install, also because you wrote that you uninstalled before trying again. Real dual boot installations don't let themselves be uninstalled that easily.

Could you give us the specs of your computer? CPU, RAM, video card, wifi if applicable, available disk space. On a seven year old computer Ubuntu may not be the right choice. Xubuntu may be better suited. It's Ubuntu in a lighter skin.

Wubi installations are mostly meant for trying Ubuntu, because they can be easily uninstalled. They don't need a partition of their own, but use a file as virtual partition instead.

Have you made sure the unreliability of your XP is not caused by hardware failure? Because in that case Ubuntu won't help. But I know that windows has a tendency of becoming unreliable, if only because of the ever increasing memory demands of anti-virus software.

---

