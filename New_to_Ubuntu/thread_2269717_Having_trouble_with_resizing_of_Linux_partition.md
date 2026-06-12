---
title: "Having trouble with resizing of Linux partition"
date: 2015-03-17
forum: New to Ubuntu
---

### Post by leonardo18 on 2015-03-17
I installed Ubuntu 14.10 in dual boot with Windows 7. 
I created a 25gb partition for ubuntu, but soon I realized I needed more than that. So I've tried to resize it with Gparted, but I apparently can't do it. 
I tried right-clicking ext-4 (image) and clicking resize, but I can't change the size of the partition, the min and max size are exactly it's present size, "free space preceding" AND "free space following" are both stuck at 0 (the first one is greyed out and the second is just stuck).
I've read that I should do something called unmounting: while I have a vague idea of what that means, I have absolutely no idea on how to do it and don't want to risk ruining my install. 
Any help would be greatly appreciated, I'm loving the OS so far and want to learn more about it, all his nooks and crannies. 
[ATTACH=CONFIG]260695[/ATTACH]

---

### Post by deadflowr on 2015-03-17
It seems you are trying this while using the partition you want to resize, is this correct?

You can use the Ubuntu installation disk, also known as a livecd, and reboot into it.

You should get an option for "Try Ubuntu" when you reboot into the livecd, use that option.

Gparted is actually on the live cd.

This will have the partitions unmounted.

In some cases, you also need to disable swap when using the livecd.
To disable swap. simply right click on the swap partition and select swapoff. 

If for some reason you ARE doing this in a livecd session, already, then you can easily unmount the ext4(Ubuntu) partition, by doing a similar method.
(Right click and choose unmount)

Note: there are always caveats to resizing any Windows partition.
I would recommend a quick review of this
[https://help.ubuntu.com/community/HowtoResizeWindowsPartitions](https://help.ubuntu.com/community/HowtoResizeWindowsPartitions)
as a quick reference point.

Also, sometimes, depending on how you resize the partitions, things can get botched, particularly with the bootloader.
Look over at this on the boot repair program, just in case.
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

Hope this helps, or at least makes sense.

---

### Post by leonardo18 on 2015-03-17
I used a usb drive that I set up with Universal Usb Installer, is it the same?
So let me see if I've understood: plug in usb>boot up>pick try ubuntu>use gparted to resize.
Is there something else I should know or is it literally "resize to X" and I'm done?
thanks for the help

---

### Post by Vladlenin5000 on 2015-03-17
You resize (expand) a partition if you have another immediately after. First you need to delete or 'move right' that other partition.

---

### Post by v3.xx on 2015-03-17
> So let me see if I've understood: plug in usb>boot up>pick try ubuntu>use gparted to resize.

That should do it and give you a full view of all partitions.  Could you post a screenshot of all partitions?

---

### Post by leonardo18 on 2015-03-17
> **v3.xx said:**
> That should do it and give you a full view of all partitions.  Could you post a screenshot of all partitions?
I did in the first post

---

### Post by leonardo18 on 2015-03-17
I posted a screenshot in the first post.
I tried what I said, but it didnt work. it just gets me to the normal "pick the os" page and then password. I didnt change the boot order so it should still be Usb first, I even formatted and re-ran UUI on the usb with the ubuntu .iso.
Goddamit

---

### Post by plucky on 2015-03-17
You should use Windows 7 tools to shrink the Windows 7 Partition.

This will create space in front of the Ubuntu Partitions.

You can now boot the USB Ubuntu install drive and use gparted to first extend the "extended partition" into the space created.

You can now move the / partition into the space created at the front.

Once the space is behind the / partition, you can now increase the size of the / partition into it.

You might have to un-mount the swap partition which the USB installer will mount before gparted will let you resize the extended partition.

Hope this makes sense.

Good Luck

---

### Post by leonardo18 on 2015-03-17
I cant boot the usb install drive. It just doesnt do it, it goes straight to letting me choose the os

---

### Post by plucky on 2015-03-18
> **leonardo18 said:**
> I cant boot the usb install drive. It just doesnt do it, it goes straight to letting me choose the os

[Gparted CD](http://gparted.org/livecd.php) can also be used. but it might be handy to have a [Boot-Repair CD](http://sourceforge.net/projects/boot-repair-cd/files/) as well before you start playing with partitions.

Also a good backup just in case anything goes wrong.

You might have to go to the boot menu to boot the USB drive.

Have you used this USB drive before to install Ubuntu?

Did you check the md5sum and verify the burn of the Ubuntu ISO?

---

### Post by leonardo18 on 2015-03-18
Why should I have a boot repair CD(don't know what it is)? 
Its the same USB stick I used before, but I formatted it and reinstalled the ISO wit UUI.
I'll try checking the boot menu when I'm home, don't know what md5sum is

---

