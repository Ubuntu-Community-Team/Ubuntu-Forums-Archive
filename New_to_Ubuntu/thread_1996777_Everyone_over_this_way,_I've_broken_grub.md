---
title: "Everyone over this way, I've broken grub"
date: 2012-06-04
forum: New to Ubuntu
---

### Post by mr-woof on 2012-06-04
Hi all,

I've got two disks, ubuntu on one and xp on the other, today I moved them both onto a new motherboard/cpu. I tried running sysprep on xp and after a while I came to the conclusion that I'd just reinstall. So fresh XP install, that boots fine, but no ubuntu. In the past, I'd use a live cd, run sudo update-grub and hey presto, grub with ubuntu and xp.

I ran the boot-repair from a live cd and ubuntu now boots, but there is no sign of grub and I can't get to xp. 

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

What the heck am I missing here, this is starting to annoy the hell out of me?

Help! :)

---

### Post by editheraven on 2012-06-04
If your ubuntu loads it means your bootloader is somewhere. You can see in whitch mbr [what hdd] it's installed by running[FONT=monospace] "[/FONT]file -s /dev/sda". Replace sda with your device.

To install grub to your first hard drive's mbr : sudo grub-install /dev/sda, where sda is again your first hdd.

---

### Post by wilee-nilee on 2012-06-04
> **mr-woof said:**
> Hi all,

I've got two disks, ubuntu on one and xp on the other, today I moved them both onto a new motherboard/cpu. I tried running sysprep on xp and after a while I came to the conclusion that I'd just reinstall. So fresh XP install, that boots fine, but no ubuntu. In the past, I'd use a live cd, run sudo update-grub and hey presto, grub with ubuntu and xp.

I ran the boot-repair from a live cd and ubuntu now boots, but there is no sign of grub and I can't get to xp. 

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

What the heck am I missing here, this is starting to annoy the hell out of me?

Help! :)
Post the bootinfo summary's HTTP address from using the boot-repair.

Run in the ubuntu install
```
sudo update-grub
```If you have not, hard to tell with the syntax, where you ran it.

---

### Post by flemur13013 on 2012-06-04
> I've got two disks, ubuntu on one and xp on the other,

Why not keep each system separate for booting?  Only windows on one disk, and only linux on the other, and you select boot via BIOS. It's really a lot easier than using grub to get at windows and having windows depend on grub. 

Just set up each disk separately with the other disk disconnected - get XP booting with their "rescue" stuff, and then install/repair ubuntu on the other disk with the windows disk disconnected.  Then hook 'em both up and select the boot disk/OS from BIOS.

---

### Post by wilee-nilee on 2012-06-04
> **flemur13013 said:**
> Why not keep each system separate for booting?  Only windows on one disk, and only linux on the other, and you select boot via BIOS. It's really a lot easier than using grub to get at windows and having windows depend on grub. 

Just set up each disk separately with the other disk disconnected - get XP booting with their "rescue" stuff, and then install/repair ubuntu on the other disk with the windows disk disconnected.  Then hook 'em both up and select the boot disk/OS from BIOS.

That is why I want the bootscript, I would bet the XP is broken, or the update-grub needs to be run in ubuntu. 

Grub boots windows with no problems.

---

### Post by mr-woof on 2012-06-04
well, I ran sudo update-grub and this time it actually picked up xp

Generating grub.cfg ...
Found linux image: /boot/vmlinuz-3.2.0-24-generic-pae
Found initrd image: /boot/initrd.img-3.2.0-24-generic-pae
Found linux image: /boot/vmlinuz-3.2.0-24-generic
Found initrd image: /boot/initrd.img-3.2.0-24-generic
Found linux image: /boot/vmlinuz-3.0.0-17-generic
Found initrd image: /boot/initrd.img-3.0.0-17-generic
Found linux image: /boot/vmlinuz-2.6.38-13-generic-pae
Found initrd image: /boot/initrd.img-2.6.38-13-generic-pae
Found linux image: /boot/vmlinuz-2.6.32-35-generic
Found initrd image: /boot/initrd.img-2.6.32-35-generic
Found Microsoft Windows XP Professional on /dev/sda1
done

reboot and still no grub, this is mental!

Edit: I see you want the url for boot-repair, I'm running it again. I've also said install grub on sdb, which is the ubuntu disk

---

### Post by drs305 on 2012-06-04
Also, try holding down the SHIFT key during the early part of the boot process to see if the menu appears.

---

### Post by mr-woof on 2012-06-04
Will do, going to reboot now and see what happens..

boot-repair paste url

[http://paste.ubuntu.com/1023866/](http://paste.ubuntu.com/1023866/)

No grub after a reboot

---

### Post by mr-woof on 2012-06-05
Just to let everyone know, I think it's the new motherboard. I've been messing around with it now for most of the day, including a fresh install of XP and then a fresh install of ubuntu and still no dual booting. 

I've officially given up and I'm now just using Ubuntu, I will never, ever buy a AS rock motherboard again.

---

