---
title: "XP and Ubuntu dual boot"
date: 2008-08-25
forum: New to Ubuntu
---

### Post by MaxMix on 2008-08-25
I am a complete newcomer to Linux. I successfully installed Ubuntu on my external USB HDD, excellent.. Unfortunately if my external USB HDD wasn't plugged in I was unable to boot the machine to any operating system. I can only assume the boot record was modified on my Windows drive.

I used the Windows disk and ran FIXMBR.. This has restored booting of Windows to normal but unfortunately there appears no way to boot Ubuntu now, not unexpected I suppose.

is there a way to 'dual boot' without effecting the Windows operating system using this configuration?

I have tried using 'boot from USB device' on system startup but no go.

Is there a way to recover the copy of Ubuntu I have sitting on my external HDD also . .

Sorry for the long waffle . .

Regards . .

---

### Post by tuxxy on 2008-08-25
Did you read the installation guide? and setup partitions on your drive for the ubuntu install?

---

### Post by django0909 on 2008-08-25
This link should sort you out.

> [http://www.howtogeek.com/howto/ubuntu/reinstall-ubuntu-grub-bootloader-after-windows-wipes-it-out/](http://www.howtogeek.com/howto/ubuntu/reinstall-ubuntu-grub-bootloader-after-windows-wipes-it-out/)

Hope you get sorted!

---

### Post by MaxMix on 2008-08-25
> **tuxxy said:**
> Did you read the installation guide? and setup partitions on your drive for the ubuntu install?

Of course . . I just wasn't expecting to be unable to boot anything with the external USB drive removed . . I think I need to take another look . .

---

### Post by django0909 on 2008-08-25
You need to reinstall GRUB and then manually edit it to include the USB drive. :)

---

### Post by MaxMix on 2008-08-25
> **django0909 said:**
> This link should sort you out.



Hope you get sorted!

Thanks  . . Although perhaps I should install onto an independent internal drive and choose which drive to boot from via the BIOS at power up. Then everything will be completely isolated . .

Good stuff . .

---

### Post by django0909 on 2008-08-25
Perhaps. It shouldn't be too hard to get GRUB to boot from the USB drive though. Remember it's GRUB you want to be using, not the Windows MBR.

---

### Post by Too Late on 2008-08-25
MBR or Master Boot Record is extremely tiny, only 512 bytes (from which the boot loader can take only 446 bytes). So it can't contain much of code, particularly it only has the location where to read the rest of the boot loader (grub in this case).

Now, you had installed the MBR section of grub into your internal HDD and the rest was on the external drive. That means that you have to plug both of them to have a working bootloader.

So now you have two options: You can make a small partition on to your internal drive, and install grub completely on to that disk. (The partition doesn't need to be larger than 100 MB.) You should automount that partition into your Ubuntu system.

OR then you can install grub completely on your external HDD. This is the easier case now, since you have already installed it there. Only the MBR section is missing. Of course, this method requires that your computer can boot from a USB disk.

Next time, you can choose the location of the "MBR section" in the very end of Ubuntu installation process. There's an Advanced button which lets you choose that location/HDD.

---

### Post by ooobuntooo on 2008-08-25
Try Wubi, the easiest way to install Ubuntu inside of Windows.

[http://wubi-installer.org/](http://wubi-installer.org/)

---

### Post by MaxMix on 2008-08-25
All sorted . . Without wishing to go through a great 'technical process'.. Simply disconnected internal SATA drive, booted Ubuntu on CD and installed onto IDE external USB drive . . At finish re-connected internal drive and can now boot either with no interference . . Simple . . Job done . .

---

