---
title: "GRUB Error 22"
date: 2008-11-11
forum: New to Ubuntu
---

### Post by Aspras on 2008-11-11
Hello, I recently resized the partition I have Ubuntu installed in by booting into the Live CD and then into the temporary desktop, I used GParted to resize it, so this is what it looks like right now.

[Image]("http://img380.imageshack.us/my.php?image=examud3.jpg") 

Ever since I resized it each time I reboot it says this when GRUB loads.

GRUB loading stage1.5

GRUB Loading please wait...

GRUB error 22

I searched the forums and the documentation also, I guess what I have to do is restore GRUB and I have found [this]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows").
Still when I run the command "find /boot/grub/stage1" it outputs
"Error 15: File not found" so I cant continue.

---

### Post by iponeverything on 2008-11-11
> **Aspras said:**
> Hello, I recently resized the partition I have Ubuntu installed in by booting into the Live CD and then into the temporary desktop, I used GParted to resize it, so this is what it looks like right now.

[Image]("http://img380.imageshack.us/my.php?image=examud3.jpg") 

Ever since I resized it each time I reboot it says this when GRUB loads.

GRUB loading stage1.5

GRUB Loading please wait...

GRUB error 22

I searched the forums and the documentation also, I guess what I have to do is restore GRUB and I have found [this]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows").
Still when I run the command "find /boot/grub/stage1" it outputs
"Error 15: File not found" so I cant continue.

boot up with a livecd to see if your partition is still there and that you can read it.

---

### Post by Aspras on 2008-11-11
I am right now using the live cd and on the temporary desktop , the image you see is a screenshot i just took.

---

### Post by bumanie on 2008-11-11
[Follow this]("httphttp://ubuntuforums.org/showthread.php?t=224351://") - it should reinstall grub. If that doesn't work, try super grub disk.

---

### Post by caljohnsmith on 2008-11-11
How about posting the output of:
```
sudo mount /dev/sda5 /mnt
ls -l /mnt
ls -lR /mnt/boot
```
Where "-l" is a lowercase L, not a one. We can work from there if you want.

---

### Post by Aspras on 2008-11-11
> **bumanie said:**
> [Follow this]("httphttp://ubuntuforums.org/showthread.php?t=224351://") - it should reinstall grub. If that doesn't work, try super grub disk.

Thanks a bunch for that link. Specifically this is what I needed to know:

Mine was a slightly different story. I couldn't get grub to find the stage1 file or even recognize my drive. So I borrowed some knowledge I picked up while using Gentoo:

You have to mount your root partition using the livecd:
Code:

$
Code:

sudo mkdir /mnt/root

$
Code:

sudo mount -t ext3 /dev/sda6 /mnt/root

Then you have to mount the proc subsystem and udev inside /mnt/root also:
Code:

$
Code:

sudo mount -t proc none /mnt/root/proc

$
Code:

sudo mount -o bind /dev /mnt/root/dev

Doing this allows grub to discover your drives. Next you have to chroot:
Code:

$
Code:

sudo chroot /mnt/root /bin/bash

Now that you're chrooted into your drive as root everything should work.
Code:

#
Code:

sudo grub

I edited in the sudo, just to be safe. When I enter grub and not sudo grub, grub cannot find the file. I do not know if the chroot changes this because I did not try it that way. In the end I figured it was better to err on the side of caution. Tosk I hope you don't mind my editing of your reply.
grub>
Code:

find /boot/grub/stage1

It found mine on (hd0,5)
Code:

grub>
Code:

root (hd0,5)

It successfully scanned the partition and recognized the filesystem-type
Code:

grub>
Code:

setup (hd0)

That was it. It installed and on reboot I was thrown back into Ubuntu.

This might help some people who are having issues so I thought I would post it.

PLEASE NOTE: My Ubuntu was installed to /dev/sda6. This may not be the same for everyone. /dev/sdaX means it's SCSI/SATA/USB/FireWire drive. And it's partition 6 because I have a weird partitioning scheme in place.

--Tosk

---

