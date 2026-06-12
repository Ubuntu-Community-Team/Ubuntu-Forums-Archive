---
title: "Windows XP not showing up in Grub after dual-boot install of 12.04 LTS"
date: 2013-09-18
forum: New to Ubuntu
---

### Post by senpai71 on 2013-09-18
First off, I apologise if this is a simple question which has already been answered. I am NOT a Linux guy - I'm a PC guy, who had to install Ubuntu for a specific purpose, and is now regretting it a little :(

So I had to run Ubuntu from a LiveCD to get my HP Touchpad working again. I subsequently decided (now, I suspect, unwisely) to install Ubuntu permanently, because it said it offered a dual-boot option with Windows XP. So I installed it as a dual-boot with my existing Windows XP, and took all the defaults - didn't change a thing, in terms of changing partitions etc.

Anyway, I am now unable to boot into Wndows XP, and I'm trying to find out why. When I'm in Ubuntu, I can see all the Windows files, so I know they're still there.

How would I find out what has 'gone wrong' and how to fix it? I think I need to change something in Grub (Grub 2), but I don't know what. Like I said, I'ma  PC guy, so the command line is pretty foreign to me.

I'm using Ubuntu 12.04 LTS

FWIW, here's the output of fdisk -l:

[FONT=courier new]Disk /dev/sda: 80.0 GB, 80000000000 bytes
255 heads, 63 sectors/track, 9726 cylinders, total 156250000 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x11d0488d

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   156232124    78116031    7  HPFS/NTFS/exFAT

Disk /dev/sdb: 320.1 GB, 320072932864 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142447 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000ef8d1

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              63   455128384   227564161    7  HPFS/NTFS/exFAT
/dev/sdb2       455129086   625141759    85006337    5  Extended
/dev/sdb5       455129088   617039871    80955392   83  Linux
/dev/sdb6       617041920   625141759     4049920   82  Linux swap / Solaris
[/FONT]
If this isn't the best place to ask, can someone please point me to the right place? All the Google searches I've seen seem to assume that the person asking the question is comfortable messing around running terminal commands, and while I have no problem doing that if it's necessary, I'd really like to have the simplest answer possible, if one exists.

I'd like to be able to dual-boot and maybe learn Linux slowly, but this hasn't helped... :)

Thanks!

---

### Post by deadflowr on 2013-09-18
Please run
```
sudo update-grub
```
from the terminal.
And if possible post the output here.

If, after the command is run, a listing shows up for Windows XP try rebooting and see if you can select it.

---

### Post by newb85 on 2013-09-18
I would suggest that you install and run boot-repair in Ubuntu.  Open a terminal (Ctrl+Alt+T) and run the following:
```
sudo add-apt-repository ppa:yannubuntu/boot-repair && sudo apt-get update[COLOR=#333333][FONT=UbuntuMono]
[/FONT][/COLOR]sudo apt-get install -y boot-repair
```

Then open boot-repair from the Dash.

For the record, contrary to what seems apparent from Apple's ad campaign, the term "PC" doesn't only refer to Windows machines.

---

### Post by whitesmith on 2013-09-18
Download and burn the BootRepair iso. Boot from it with all defaults taken. Sometimes it fixes boot problems on its own. To be on the safe side, write down the URL it displays at the end of the repair process. If there's still a problem, post that URL here so we can have a look at the report.

---

### Post by senpai71 on 2013-09-18
> **deadflowr said:**
> Please run
```
sudo update-grub
```
from the terminal.
And if possible post the output here.

If, after the command is run, a listing shows up for Windows XP try rebooting and see if you can select it.

deadflowr,

OK, so that fixed it - simply runnign update-grub made it find my WinXP.

First off, thanks very much!
Second, sorry if it was very easy for you guys - I hope I didn't waste anyone's time.
Third, is this to be expected? I would assume that if I install Ubuntu, it would do this as part of the setup... Should I, as a Linux noob, have known to run this manually post-install?

Thanks again,

senpai71

---

### Post by deadflowr on 2013-09-18
In terms of running the update-grub command post install, normally you shouldn't have to.
But once in a blue moon, when the system is installing and it is suppose to get to that point sometimes is misses it.
But luckily for you that's all that happened.
Worst case, after a partition wipe(of course), would be the lost of the windows boot files.
Those can be repair easily, but you'd need to go to microsoft for help with that.

---

### Post by mastablasta on 2013-09-18
> **deadflowr said:**
> Those can be repair easily, but you'd need to go to microsoft for help with that.


indeed. as in linux to fix this in windows it's a short one line command.

sometimes Grub is placed in the wrong place. by installer or unknowingly by the user installing the OS. they've made a nice GUI tool for those that don't like command line: [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)  it will fix this as well as many other boot issues.

ofcourse on a single OS install there is no such issue ;-)

---

