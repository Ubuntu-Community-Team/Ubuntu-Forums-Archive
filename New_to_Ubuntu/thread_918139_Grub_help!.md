---
title: "Grub help!"
date: 2008-09-12
forum: New to Ubuntu
---

### Post by ergonomicben on 2008-09-12
Just installed ubuntu, but didn't install grub as i want to dual boot with vista 64 so i want to install grub to a separate partition /dev/sda4 how would i do this through the terminal?

---

### Post by WRDN on 2008-09-12
Follow [this]("https://wiki.ubuntu.com/RecoveringUbuntuAfterInstallingWindows") guide to install/ reinstall GRUB.

---

### Post by ergonomicben on 2008-09-12
Sorry i'm sure the answer is in the link but they're are so many options i'm not quite sure which one is right for me. i'm trying to get grub on a separate partition from ubuntu and vista, so i can use easybcd to configure my boot settings from windows ...any pointers??

---

### Post by ubername on 2008-09-12
> **ergonomicben said:**
> Just installed ubuntu, but didn't install grub as i want to dual boot with vista 64 so i want to install grub to a separate partition /dev/sda4 how would i do this through the terminal?

Hi

You don't need to install grub to a separate partition to dual boot with anything.
Grub works in the MBR (Master boot record) of the drive from which you boot, and can point to any partition on that (or other ) drive.

 If you have a straightforward set-up with e.g. vista on one partition and ubuntu on another one (or more, depending on how you want to handle / and /home) and a swap partition, grub will handle it fine.

If you have more than one bootable drive (e.g. windows on a hard drive, and linux on a USB drive) it becomes a bit, but not much, harder. you just need to know which drive you are booting from and edit the menu.lst in /boot/grub to make sure you are pointing at the right files.

It's hard to explain so here is some of my menu.lst which may help

title Possibly Safe Intrepid on HDD
root (hd1,1)
kernel (hd1,1)/boot/vmlinuz-2.6.27-2-generic root=UUID=eda1f21c-3655-4563-9981-3cc1d5dd4093
initrd (hd1,1)/boot/initrd.img-2.6.27-2-generic

title If needs be try Vista
root (hd1,0)
chainloader +1
savedefault
makeactive

title		Ubuntu intrepid (development branch), kernel 2.6.27-3-generic
root		(hd0,2)
kernel		(hd0,2)/boot/vmlinuz-2.6.27-3-generic root=UUID=945d356d-ab6b-4f99-8327-3590f57de729 ro quiet splash 
initrd		(hd0,2)/boot/initrd.img-2.6.27-3-generic
quiet

To explain: I have a USB drive which is always switched on and can be booted, so that is hd0. on that USB drive I have a number of partitions of which the bootable linux partition is 2 (partition 0 is windows storage and partition 1 is linux storage).

I also have a hard disk (of course) which is (from the perspective of the USB drive) hd1. On this I have a Windows partition (hd1,0) and a linux partition (hd1,1)

I can access all these from the grub installed on my USB, looking at the MBR on the USB.

Hope this helps, and honestly, it isn't as difficult as this might all sound. Let your system work for itself, and use the grub set-up that the LiveCD installs. Although I haven't used it myself, I believe grub-update might be able to help you

(sudo grub-update from the terminal)

Hope this helps.

---

### Post by ergonomicben on 2008-09-12
yeah i'm starting to think that would be easier, problem is all these guides assume grub has been installed and just needs to be found again, problem is i never installed it to begin with! what do i need to do to install it? ("sudo grub-update" was an unknown command)

---

### Post by ubername on 2008-09-12
> **ergonomicben said:**
> yeah i'm starting to think that would be easier, problem is all these guides assume grub has been installed and just needs to be found again, problem is i never installed it to begin with! what do i need to do to install it? ("sudo grub-update" was an unknown command)

Go to System>Administration>Synaptic Package Manager. Enter your password. Search for 'grub'. select the 'grub' package. I also have the qgrubeditor package selected as that provides an easier (but not complete) way of editing the menu.lst. I find the best thing is to use a combination of qgrubeditor and a plain text editor (in sudo mode) for menu.lst. eg gksu gedit /boot/grub/menu.lst

BTW, I have just downloaded and run easyBCD from my 64 bit vista setup. It wasn't at all happy with my set-up: it couldn't find the USB drive or the 'C:\' drive that I was booting from. Are there any particular features of easybcd you would like?

---

### Post by ergonomicben on 2008-09-12
Well in the end i've just did a quick reinstall of the whole of ubuntu, putting grub where i should have done to begin with (with ubuntu).

I thought i'd use easybcd, because of some recommendations for being easier to use with vista, as vista "apparently" will want to keep "fixing" the bootloader so losing grub on updates, i may however be misinformed!

I think it will be fine for my simple setup, but i can see how it won't be good for yours.

Thanks for all your help anyway! :)

---

### Post by ubername on 2008-09-12
> **ergonomicben said:**
> Well in the end i've just did a quick reinstall of the whole of ubuntu, putting grub where i should have done to begin with (with ubuntu).

I thought i'd use easybcd, because of some recommendations for being easier to use with vista, as vista "apparently" will want to keep "fixing" the bootloader so losing grub on updates, i may however be misinformed!

I think it will be fine for my simple setup, but i can see how it won't be good for yours.

Thanks for all your help anyway! :)

No probs.

I've had no issues with vista trying to change my MBR and I've been through a couple of updates for vista, so I wish you well. Post again with any more issues - I am a relative newbie and get massive support from the people on these forujms.

---

