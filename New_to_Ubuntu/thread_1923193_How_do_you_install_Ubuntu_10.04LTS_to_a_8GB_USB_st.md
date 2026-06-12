---
title: "How do you install Ubuntu 10.04LTS to a 8GB USB stick?"
date: 2012-02-10
forum: New to Ubuntu
---

### Post by suomalainen on 2012-02-10
Ubunteros,

I would like to install Ubuntu 10.04LTS to a USB 8 GB stick. I want to also be able to save all and any settings that are made and not have to re-enter them each time I boot up. I also want to download security updates when available.

If you know a good online tutorial that can help me that would be greatly appreciated to know about.

Thanks!

---

### Post by shakabra on 2012-02-10
If you are using Ubuntu now then you can use Ubuntu's 'Startup Disk Creator' if not use unetbootin [http://unetbootin.sourceforge.net/]("http://unetbootin.sourceforge.net/") They are both pretty self-explanatory.

---

### Post by Linuxisfast on 2012-02-10
When you create the live USB, increase the amount of persistent storage to the capacity of your USB stick so that you can store data in it.

---

### Post by mike555 on 2012-02-10
or just install to the usb, but be sure to install grub to same usb (not MBR)

---

### Post by bogan on 2012-02-10
Hi! **suomalaine**n, 

You Posted:>  If you know a good online tutorial that can help me that would be greatly appreciated to know about. There is an exhaustive tutorial  at: [http://ubuntuforums.org/showthread.php?t=1650699&highlight=avoid+wubi+install+ubuntu+USB+drive](http://ubuntuforums.org/showthread.php?t=1650699&highlight=avoid+wubi+install+ubuntu+USB+drive)

This is not for the minimal installation you get from "make a Startup Disk", but a full one of any size you choose, 8GB is ideal.

 I made mine with a Linux partition of 4.5GB, a 2GB Swap file and a 1GB Fat32 Switch file that  auto mounts and is accessible from other installations. 

Works a treat as a certain BACK-UP with all the essential drivers already installed andconfigs set-up..

Chao!,** bogan**.

---

### Post by sudodus on 2012-02-10
You should decide if you want a 'normal' install or a persistent live system. Both are possible, but a 'normal' install is better if you want to do a lot of updating and installing (and necessary if you want to update the kernel).

With a normal install you should mount the system drive with noatime to avoid wearing it with to much writing (USB sticks cannot be written as many times as a HDD).

I have a persistent Lubuntu USB drive, described in this link
[[COLOR="Red"]_http://ubuntuforums.org/showthread.php?t=1885392_[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1885392")

---

### Post by suomalainen on 2012-02-10
I just finished using "'Startup Disk Creator" to install Ubuntu 10.04 onto my USB stick.

When I try to boot it the following error pops up.

See attached picture for details.

What can I do to fix this?

---

### Post by C.S.Cameron on 2012-02-11
> **suomalainen said:**
> I just finished using "'Startup Disk Creator" to install Ubuntu 10.04 onto my USB stick.

When I try to boot it the following error pops up.

See attached picture for details.

What can I do to fix this?

I believe this can be associated with a corrupt iso download, check the MD5SUM.

---

### Post by suomalainen on 2012-02-11
I strongly doubt this as the disk has been used on numerous occasions to perform flawless installs.

---

### Post by bcousins on 2012-02-11
> **suomalainen said:**
> I strongly doubt this as the disk has been used on numerous occasions to perform flawless installs.

It looks like Grub is Missing, You might want to re-install Ubuntu.

---

### Post by suomalainen on 2012-02-11
All,

I'm following the instructions as provided here:

[https://wiki.ubuntu.com/LiveUsbPendrivePersistent](https://wiki.ubuntu.com/LiveUsbPendrivePersistent)

I need to have persistence.

After everything is done I reboot and get the error I told you about.

DOn't know what to do next.

---

### Post by suomalainen on 2012-02-11
Don't know if this is contributing to the problem but I'm using a Huawei e367 broadband stick into which I have inserted a 8GB micro sd card. On this I install Ubuntu.

Also, each time I boot my machine the preinstalled operator software that is installed on the stick appears on the desktop.

Maybe these details help?

---

### Post by sudodus on 2012-02-11
> **suomalainen said:**
> All,

I'm following the instructions as provided here:

[https://wiki.ubuntu.com/LiveUsbPendrivePersistent](https://wiki.ubuntu.com/LiveUsbPendrivePersistent)

I need to have persistence.

After everything is done I reboot and get the error I told you about.

DOn't know what to do next.
You should decide if you want a ***'normal' install but to the USB drive*** or a persistent live system. Both are possible, but a 'normal' install is better if you want to do a lot of updating and installing (and necessary if you want to update the kernel).

With a 'normal' install you should mount the system drive with noatime to avoid wearing it with to much writing (USB sticks cannot be written as many times as a HDD).

I have a persistent Lubuntu USB drive, described in this link
[[COLOR="Red"]_http://ubuntuforums.org/showthread.php?t=1885392_[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1885392")

I think it is worth trying ***unetbootin***. I have good experience booting several different computers with USB drives made with unetbootin. Since you want persistence, it is really an alternative to 'install' the system, but if you want portability to other computers, don't install proprietary drivers!

---

### Post by sudodus on 2012-02-11
We were writing our last posts at the same time: Yes, I think the Huawei stick might complicate the booting. I suggest you try booting from a 'normal' USB drive (a flash stick or a HDD would work normally)

---

### Post by suomalainen on 2012-02-11
Uummm... I got ubuntu already installed but it ain't booting up.

---

### Post by sudodus on 2012-02-11
Is your problem that the computer won't boot from its internal drive? Or do you want to portable drive with your personal system?

Have you tried different versions and flavours of Ubuntu or maybe Linux Mint?

---

### Post by C.S.Cameron on 2012-02-11
Can you try your stick on a second computer?

---

### Post by suomalainen on 2012-02-11
I guess I failed to articulate what my problem is?

As I noted above, I installed Ubuntu 10.04 LTS onto a 8GB microSD card that resides on my usb broadband stick.

When I re-boot the laptop the error message I attached pops up. There is no internal HDD or external HDD attached to the laptop during this time.

The outcome that I wold like to see is that my usb stick boots up accordingly.

Thank you for your understanding

---

### Post by sudodus on 2012-02-11
Thanks for making it clear:-) Then I repeat: The Huawei stick might complicate the booting. I suggest you try booting from a 'normal' USB drive.

*Edit: And when booting works from a 'normal' USB drive, you can try with a cloned copy of that in your microSD card that resides on your Huawei usb broadband stick if you want to travel light (with only one USB device)*

---

### Post by suomalainen on 2012-02-11
But I don't want to do that :) ! I want everything consolidated onto one stick and have plug & go device...  I do not want to carry two devices. I.E. broadband stick and usb stick...

I'll get this to work. just got to find the individual that knows how it's done or the online resources that show how to... that simple.

---

### Post by sudodus on 2012-02-11
Yes, but maybe do it step-wise ... as I was editing in my previous post, again posting at the same time as you ;-)

---

### Post by C.S.Cameron on 2012-02-11
Following step by step for Full install of 11.04 or 11.10 to USB device.
Partition sizes given are for 8GB drive, adjust size to suit:

Turn off and unplug the computer. (See note at bottom)

Remove the side from the case.

Unplug the power cable from the hard drive.

Plug the computer back in.

Insert the USB drive.

Insert the Live CD or Live USB.

Start the computer, the CD / flash drive should boot, (you need to adjust BIOS to boot USB).

Select language and "Install Ubuntu"

Select Download updates while installing and Select Install this third-party software.
(Notice that at least 4.4 GB drive space is required for 11.10, 4GB bootable flash drive users must choose another distro for a full install).

Forward or Continue

If prompted unmount partitions.

Select "Something else"

Forward or Continue

Confirm "Device for boot loader installation:" is correct, (If you left your internal HDD plugged in make sure the USB drive root is selected - sdb not sdb1).

(Optional Windows data partition)

Select "New Partition Table" click Continue on the drop down.

Click "Free space" and "Add".

Select "Primary".

Make "New partition size..." about 1000

"Location = Beginning".

"Use as: = FAT32 file system"

And "Mount point = windows".

Select "OK"

Click "free space" and then "Add".

Select "Primary", "New partition size ..." = 3 to 4 GB, Beginning, Ext4, and Mount point = "/" then OK.

(Optional home partition)

Click "free space" and then "Add".

Select "Primary", "New partition size ..." = 1 to 2 GB, Beginning, Ext2, and Mount point = "/home" then OK.

(Optional swap partition)

Click "free space" and then "Add".

Select "Primary", "New partition size ..." = remaining space, (1 to 2 GB), Beginning and "Use as" = "swap area" then OK.

(Importent)

Confirm "Device for boot loader installation" points to the USB drive. Default should be ok if HDD was unplugged.

Click "Install Now".

Select your location.

Forward.

Select Keyboard layout.

Forward.

Insert your name, username, password, computer name and select if you want to log in automatically or require a password.

Selecting "Encrypt my home folder" is a good option if you are worried about loosing your USB drive.

Select forward.

Wait until install is complete.

Turn off computer and enable the HDD.

Stick the side panel back on.

Note:
You may omit disabling the hard drive if after partitioning you choose to install grub to the root of the usb drive you are installing Ubuntu to, (ie sdb not sdb1). Be cautious, many people have overwritten the HDD MBR.

---

