---
title: "Dual Boot:  Ubuntu and Windows 10 - Grub Boot-Repair Help"
date: 2017-04-23
forum: New to Ubuntu
---

### Post by rmarcotte on 2017-04-23
Hello - this is my first post.  Any help is appreciated.

I have run into what seems to be the fairly common problem of the grub boot system getting corrupted in a dual-boot (Ubuntu/Windows10) environment.

Following directions, I created and booted Ubuntu Live via a USB stick.  I am able access the Windows directories on the HDD via Ubuntu Live and the files are in-tact.  I then installed and executed Boot Repair which successfully ran, but did not fix the problem - after a reboot I still cannot get to either Ubuntu or Windows on my HDD.

I then ran Boot-Repair again and got a BootInfo summary which is pasted here:  [http://paste2.org/2IBMp3WD](http://paste2.org/2IBMp3WD)

Can anybody help me either repair or reinstall grub?

Thanks in advance.

Ryan

---

### Post by TheFu on 2017-04-23
Welcome to the forums.

Looked over the bootinfo. Thanks.
I wonder what happened to sdb, sdc, sdd, sde .... it is only showing sdf ... I've never seen that before.  On this system, I'd expect the HDD connections to be sdb.

```

error: cannot read `/dev/sdf': Input/output error.
error: cannot read `/dev/sdf': Input/output error.
error: cannot read `/dev/sdf': Input/output error.
error: cannot read `/dev/sdf': Input/output error.
```

That isn't good either.  Check the controller, cables, and disk drive. If there is any data on it that you want to keep, back it up ASAP.

It appears this system is using legacy BIOS to boot, not UEFI. Is that correct?

---

### Post by termibuntu on 2017-04-23
Hello. It may seem that you need to recover grub and reinstall it. If so, follow this tutorial (I didn't write this) : [http://howtoubuntu.org/how-to-repair-restore-reinstall-grub-2-with-a-ubuntu-live-cd](http://howtoubuntu.org/how-to-repair-restore-reinstall-grub-2-with-a-ubuntu-live-cd)
hope this helps :)

---

### Post by oldfred on 2017-04-23
> Windows is hibernated, refused to mount.
This confuses everything.

And with BIOS/MBR about the only way to fix it is to boot Windows and turn off the fast start up. But grub will not boot hibernated Windows.
So you have to temporarily restore the Windows boot loader, turn off fast start up, and then restore grub.
Windows will keep turning fast start up on, on updates, so make sure it is off. And have the Windows repair disk & Ubuntu live installer always available to make it easy to restore boot loaders. Better to have two drives so you can have different boot loader or new UEFI system that can directly boot either system from UEFI.

       Fast Start up off (always on hibernation)
[http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472](http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472)
[http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html](http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html)
[URL="http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html"]http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html

[/URL]
 How to restore the Ubuntu/XP/Vista/7/8/10 BIOS bootloader 
[https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader](https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader)
[https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System](https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System) 

If Boot-Repair sees  your Windows is may let you install a Windows like boot loader using advanced mode, but usually Linux will not correctly see Windows that is hibernated or if it needs chkdsk.

Your system is promoting flash drive to sda and internal drive to sdf? That is unusual and whenever you install grub you cannot use any auto install option as those all default to install grub to sda, corrupting live installer.

[URL="http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html"]
[/URL]

---

