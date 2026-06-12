---
title: "Ubuntu Not Booting From Usb"
date: 2013-06-26
forum: New to Ubuntu
---

### Post by thenorm on 2013-06-26
Hello, I recently deleted my ubuntu partitions from windows 7 to install it again.

I deleted the partitions
Rewrote MBR with easy bcd
burned ubuntu 12.04 image with lili usb creator and tried unetboot
restarting and pressing F12 to get to boot manager and selecting usb
and windows just loads up?

I installed ubuntu the first time with this method, now its not reading the usb at start up?

thanks in advance! using toshiba satellite laptop series L655D-S5050 running windows 7

[solved] i had usb support turned off in advance menu of the BIOS. Thank you all for the support!

---

### Post by sanderj on 2013-06-26
Maybe the USB stick is not bootable at all? Have you tried in another computer?

And: no UEFI BIOS activated? I believe you need 64-bit Ubuntu for that (and possibly turn off secure boot)?

And if USB still fails ... can you write a DVD?

---

### Post by thenorm on 2013-06-26
> **sanderj said:**
> Maybe the USB stick is not bootable at all? Have you tried in another computer?

And: no UEFI BIOS activated? I believe you need 64-bit Ubuntu for that (and possibly turn off secure boot)?

And if USB still fails ... can you write a DVD?

I've used the San cruzer to install from USB the first time so I know it works. I don't know anything about uefi bios or turning secure boot off?

---

### Post by sanderj on 2013-06-26
#SanCruzer: do you mean this USB stick with this install does boot into Linux in other computers?

---

### Post by thenorm on 2013-06-26
> **sanderj said:**
> #SanCruzer: do you mean this USB stick with this install boot into Linux in other computers?

Yes I'm referring to the USB stick. I don't have access to another comp ATM. I've installed Ubuntu previously with the same USB stick and it worked. 

 I deleted Ubuntu partitions and am now trying to reinstall Ubuntu with bootable usb like before. But when I select USB from the bios windows just loads. Am using the 64 bit ver and I can't burn the iso as I keep getting read errors.

---

### Post by sanderj on 2013-06-26
OK. Boot into Windows, put in the USB stick, open Explorer: what do you see on the USB stick?

---

### Post by thenorm on 2013-06-26
> **sanderj said:**
> OK. Boot into Windows, put in the USB stick, open Explorer: what do you see on the USB stick?
I'm out right now and I'll upload screens when I get back. But its in removable storage. Showing mylinux key to install. The virtual key lili USB creator makes.

---

### Post by Vormeph on 2013-06-26
The problem couldn't really lie with UEFI because the OP doesn't have Windows 8 installed. Indeed, you should make sure that your USB's boot priority is at the highest, even above the hard drives. I'm aware that there are problems with using Universal USB Installer since it's quite pessimistic in how distros are burnt to USB. I recommend Unetbootin because of the flexibility. Have you tried burning ANOTHER distro to your USB and see if it boots up?

---

### Post by thenorm on 2013-06-26
> **Vormeph said:**
> The problem couldn't really lie with UEFI because the OP doesn't have Windows 8 installed. Indeed, you should make sure that your USB's boot priority is at the highest, even above the hard drives. I'm aware that there are problems with using Universal USB Installer since it's quite pessimistic in how distros are burnt to USB. I recommend Unetbootin because of the flexibility. Have you tried burning ANOTHER distro to your USB and see if it boots up?

Yes Linux mint 15 64 bit. 

USB is set at highest priority

I've tried with both lili and unetbootin. 

I select USB and windows just boots normally. 

I know the USB port and stick work as I've used both before to install Ubuntu.

---

### Post by thenorm on 2013-06-26
[solved] i had usb support turned off in advance menu of the BIOS. Thank you all for the support!

---

