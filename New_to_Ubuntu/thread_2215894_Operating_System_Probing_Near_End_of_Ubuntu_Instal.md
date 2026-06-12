---
title: "Operating System Probing Near End of Ubuntu Install"
date: 2014-04-08
forum: New to Ubuntu
---

### Post by KAWill70 on 2014-04-08
Does the Ubuntu installation process probe for all other operating systems accessible to the CPU that are then put into the Grub boot menu?

I see the message "Looking For Other Operating Systems" near the end of the Ubuntu installation.  Earlier I had the idea that an installation only added to any existing menu via some configuration file and just trusted that the others were really there.

Today I had a very interesting experience which makes me believe that the probing is how it is done.  I wanted to get rid of several Linux installations and reinstall some others.  The disk was formatted and I was ready to start fresh.  However, I recreated the size of several partitions exactly as they had been before.  It looks like all the data remained intact because after the first installation, all the previous Linux installations that were not overwritten appeared in the Grub boot menu.  In addition, they all worked!

This also suggests that one needs the proper procedure to remove any undesired Linux installations.

---

### Post by su:bhatta on 2014-04-09
Yes, there is the os-prober.
At the end of the installation it searches for all the OS's that are present and adds them to the grub menu.

You can edit the grub file generated and change various aspects of the grub. 
If you want you can change the default entry and set different time out, delete any entry etc.

---

### Post by KAWill70 on 2014-04-09
Thanks for the help.

At the end of the OS Probing I hope all entries are verified as existing and they are not including items that they only assume are there.

I'll look into editing the grub file as I would like to make some menu changes.

I had a situation recently where Grub crashed and it was the result of trying to remove a Linux installation without changing the Grub menu first.  A partition was deleted and Grub could not find the installation.  I'm guessing that one should manually remove installations from the Grub boot menu before deleting any related files, directories, or partitions.  If anyone is aware of a better procedure please pass it along.

---

### Post by su:bhatta on 2014-04-09
I was booting Win8, KaOS,eOS and Ubuntu Studio. 
I had wiped off my KaOS and eOS partitions. Next when I booted into Ubuntu, it showed all the missing OS's in Grub entry cause I had not run update-grub.
Today, when I installed the Beta2 of Ubuntu Studio it succesfully found only 1 entry. that of the Win8.

In case you delete some OS, it is best to enter the OS whose Grub is installed and run 

```
sudo update-grub 

```

When a fresh grub-update is run, os-prober comes into play again and it succesfully finds out what other OS's are there in the system.
In case you delete the OS whose Grub you were using, you can use the Live CD of Ubuntu (or the OS presently installed) and run boot-repair from the Live session. That will fix your grub entry.

There is a nice thread on customizing Grub here on the froums, I think it has now been converted into a Wiki too.
Just search Grub2 customizing and you should end up with it

---

### Post by grahammechanical on 2014-04-09
> [COLOR=#000000]all the previous Linux installations that were not overwritten appeared in the Grub boot menu. In addition, they all worked![/COLOR]

I do not think that formatting a partition removes any data from the partition. Neither does deleting a file. If the partition still exists then Grub os-prober can find it and look for a /boot folder and if it still exists and os-prober can identify Linux kernels and read a grub.cfg in that folder, then what you have noticed will happen.

Otherwise, data recovery utilities would not work very well.

> [COLOR=#252525][FONT=Helvetica Neue]As a general rule,[/FONT][/COLOR][COLOR=#252525][FONT=Helvetica Neue] formatting a disk leaves most if not all existing data on the disk medium; some or most of which might be recoverable with special tools.[/FONT][/COLOR]

> [COLOR=#252525][FONT=Helvetica Neue]To actually "erase" everything requires overwriting each block of data on the medium; something that is not done by many PC high-level formatting utilities.[/FONT][/COLOR]

[http://en.wikipedia.org/wiki/Disk_formatting](http://en.wikipedia.org/wiki/Disk_formatting)

Regards.

---

### Post by KAWill70 on 2014-04-09
Thanks to grahammechanical and bhattabhishek for the additional information.  Very much appreciated.

I found the Wiki article that was mentioned and will study it in detail.

[https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen](https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen)

---

