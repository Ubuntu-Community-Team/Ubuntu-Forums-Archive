---
title: "Updating GRUB doesn't change GRUB entries"
date: 2013-12-11
forum: New to Ubuntu
---

### Post by ogp on 2013-12-11
Hello, 

I'm trying to install a later version of Ubuntu to my machine. it won't boot from a USB stick and the last version of Ubuntu is too big to install from a CD so I have tried to boot from an ISO on the hard drive. I have tried two methods, one using grml-rescueboot as described here (about 1/2 way down the page): 

[https://help.ubuntu.com/community/Grub2/ISOBoot#grml-rescueboot](https://help.ubuntu.com/community/Grub2/ISOBoot#grml-rescueboot)

This worked in every sense (including seeing the lines "Found Grml ISO Image: <path_to_image/image.iso>" after entering "sudo update-grub") apart from the fact that when I rebooted, there was no new entry in GRUB. 

I then tried this method, using unetbootin to achieve much the same thing; 

[http://www.webupd8.org/2011/02/how-to-boot-iso-with-grub2-easy-way.html](http://www.webupd8.org/2011/02/how-to-boot-iso-with-grub2-easy-way.html)

Again, there was no new entry in the GRUB menu when I rebooted. 

This is leading me to wonder whether I have two versions of GRUB on my machine and am somehow updating the wrong version - or updating something other than that which it is booting from. (That may not be explained well.) I have had many versions of Ubuntu on this machine over the last few years and there are two separate hard drives, each with multiple partitions. Could this be relevant? 

I'm currently running (and working from) Ubuntu Studio 13.10 with KDE, and am trying to create a fresh install of Ubuntu-Gnome 13.10. The version of GRUB that I can see on boot is GRUB 2. 

All help welcomed - thank you. 


Oli.

---

### Post by Dennis N on 2013-12-11
Get a boot info summary by installing and running the boot repair tool. It should give you the information to tell what is going on.

[http://ubuntuforums.org/showthread.php?t=1769482](http://ubuntuforums.org/showthread.php?t=1769482)

---

### Post by ogp on 2013-12-12
Dennis, 

Ah, YannBuntu's Boot Repair. I hadn't thought of using that - thanks. 

Having run it, I can see the result here;

[http://paste.ubuntu.com/6560650/](http://paste.ubuntu.com/6560650/)

And from that it looks like I have two versions of GRUB running, one on sda and one on sdb. The one on sda looks like the one I want to be using as it has the entries for GRML in it, but the computer is using the GRUB on sdb. 

How do I tell the computer to use the GRUB on sda instead of the one on sdb? 

Thanks, 


Oli.

---

### Post by ogp on 2013-12-12
Dennis, 

Ah, YannBuntu's Boot Repair. I hadn't thought of using that - thanks. 

Having run it, I can see the result here;

[http://paste.ubuntu.com/6560650/](http://paste.ubuntu.com/6560650/)

And from that it looks like I have two versions of GRUB running, one on sda and one on sdb. The one on sda looks like the one I want to be using as it has the entries for GRML in it, but the computer is using the GRUB on sdb. 

How do I tell the computer to use the GRUB on sda instead of the one on sdb? 

Thanks, 


Oli.

---

### Post by grahammechanical on 2013-12-12
There are a couple of things to keep in mind.

1) the last version of Ubuntu to be installed will put its Grub into the MBR of sda. The installer defaults to putting Grub into the MBR of sda unless we point it into another direction.

2) Running update-grub will update the Grub configuration files on the partition that we are running Ubuntu from.

3) to get the changes to take effect we sometimes need to run

```
sudo grub-install /dev/sda
```

to re-install Grub to the MBR of sda. Change /dev/sda accordingly.

For example if you want Ubuntu (13.10) on sda2 to put its Grub into the MBR of sda, then load into that Ubuntu and run

```
sudo update-grub
```
```
sudo grub-install /dev/sda
```

If you want the Ubuntu (13.10) on sdb2 to put its Grub into the MBR of sdb, then load into that Ubuntu and run

```
sudo update-grub
```
```
sudo grub-install /dev/sdb
```

In find it easier to have the Ubuntu on sda controlling the MBR of sda and the Ubuntu on sdb controlling the MBR of sdb and then to use the BIOS to select a hard disk to boot from. Also, at the Grub menu if we press E we put Grub into Edit mode and we can see the boot parameters and see which kernel we are booting and from which partition. So, hd0,msdos2 would be the first hard disk and the second partition on the hard disk.

Regards.

---

### Post by Dennis N on 2013-12-12
You need to make sda the disk drive to boot at startup in the BIOS and to use the grub.cfg (which produces the menu you see) from Ubuntu 13.10 on sda2,  grub has to be installed from that OS on sda2. 

You would not boot to sdb but can leave it as it is.

On your summary, I don't understand the reference to partition 94 in the boot info summary at the start. Mine looks like this, and clearly indicates grub gets its boot files (including grub.cfg) from msdos6, which is partition 6, so I know which OS grub is making the menu and running the show.


```
============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos6)/boot/grub on this drive.

```

Suggestions:

Run **sudo update-grub** from Ubuntu on sda2 to get the menu up to date.

If something is not right, you could reinstall grub from Ubuntu 13.10 on sda2 if needed, followed by sudo update-grub. 

**sudo grub-install /dev/sda**
**sudo update-grub**

Keep in mind, I am not a expert, but can only say these are what I would consider reasonable steps. You have to be the final judge.

---

### Post by oldfred on 2013-12-12
Boot-Repair did make this suggestion:
> Please do not forget to make your BIOS boot on sda (750GB) disk!


   I do not like this suggestion with mulitple installs on muliple dirves. I prefer each install has its boot loader on its drive as suggested above and you set default boot in BIOS to one you prefer, but alway could change to the other if major issues.

> This setting would reinstall the grub2 of sda2 into the MBRs of all disks (except USB without OS).

    

You can uncheck auto repair in Boot-Repair and manually select an install and drive to install that boot loader into. But I think the instructions as posted by grahammechanical & Dennis N to just do the grub install from inside your Ubuntu are easier.

---

