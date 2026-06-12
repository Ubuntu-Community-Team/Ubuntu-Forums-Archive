---
title: "Install partition after installing Ubuntu?"
date: 2008-09-14
forum: New to Ubuntu
---

### Post by A-dogg on 2008-09-14
I have Hardy installed on my 80 gig Vaio laptop and have been using Virtualbox to run an XP system. But I want to ditch Virtualbox and install a partition on the drive so I can then install XP directly onto it. Is there a way to do create a second partition for a dual-boot (or whatever the term is) after I already have my drive formatted for one system? I've read about GParted, which looks like it MAY do it, but am utterly completely confused...

Can anyone offer any advice?

---

### Post by Jarr0d on 2008-09-14
After a quick Google I pulled out this.
[https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)

It is using GParted and has step by step guide on how to do it. Including screen shots. 

If this doesn't help, what exactly is confusing you?

---

### Post by Tatty on 2008-09-14
Yes gparted will re-partition your drive for you easily, however your system will need to be unmounted before this can work.

Simply boot into a liveCD then go to System->Administration->GNOME Partition Editor  (or something along those lines)

---

### Post by A-dogg on 2008-09-14
OK, so Tatty, you're saying I should use GNOME Partition Editor, instead of GParted? Also, I don't see that in Administration menu (maybe because I'm not currently booted from a LiveCD?). Also, I'm downloading the GParted Live USB disk, which will boot from USB, so I guess that'll unmount the drive.

Jarr0d -- Thanks for the info! The only reason what you sent me was a little confusing is because it explains how to install Ubuntu on a computer running Windows. I want to do the opposite...

Thanks guys. Whatever the opposite of computer savvy is? That's me. I'm the anti-Geek Squad.

---

### Post by Victormd on 2008-09-14
> **A-dogg said:**
> OK, so Tatty, you're saying I should use GNOME Partition Editor, instead of GParted? Also, I don't see that in Administration menu (maybe because I'm not currently booted from a LiveCD?). Also, I'm downloading the GParted Live USB disk, which will boot from USB, so I guess that'll unmount the drive.

The partition editor and gparted are the same thing. If you're NOT using the live CD and want to use Gparted, you need to install it:
```
sudo apt-get install gparted
```
Then it will show up under SYSTEM>ADMINISTRATION. However, like Tatty stated, you will need to resize from the Live CD because you can't resize a mounted HD. There's no need to download the Gparted Live CD or USB disk (unless you don't have the live CD).

More so, for what you want to do, you will need to download the [Supergrub CD]("http://www.supergrubdisk.org/") so you can fix your boot. This will be required because windows does not recognize linux and therefore, you will not be able to boot ubuntu once you install Windows (the install order should always be Windows then Linux).

---

### Post by A-dogg on 2008-09-15
So which do I do first, run GParted (from Live USB or Live CD) or run Supergrub CD (to fix the boot)? I'll have to research the Supergrub CD to see how to get it to do the "fix" you're suggesting...

I downloaded the GParted Live USB since I don't think I have the Live CD... But you're saying that the Live CD has GParted on it?

Thanks for all the help!

---

### Post by Tatty on 2008-09-15
> **A-dogg said:**
> So which do I do first, run GParted (from Live USB or Live CD) or run Supergrub CD (to fix the boot)? I'll have to research the Supergrub CD to see how to get it to do the "fix" you're suggesting...

I downloaded the GParted Live USB since I don't think I have the Live CD... But you're saying that the Live CD has GParted on it?

Thanks for all the help!

Yes, The Ubuntu Live CD has GParted installed on it by default (although it is listed in the Administration menu as the GNOME Partition Editor, or something like that).

Dont worry about supergrub just yet.  You will not need it until after you install windows.  Windows will overwrite your MBR with its own, so your comp will boot directly into windows.  You will then need to re-install grub using either the supergrub CD, or the ubuntu liveCD

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

