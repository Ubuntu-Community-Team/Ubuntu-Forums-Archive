---
title: "How to boot from usb"
date: 2014-10-20
forum: New to Ubuntu
---

### Post by guadaatenea on 2014-10-20
I'm having trouble to get a pre-installed Win8 laptop to boot from USB. I had been able to do it before and I've been reading forums and tutorials for the last two hours, but can't find the option again.
I was able to reach UEFI boot options. But USB doesn't seem to be an option. Actually, I have no other options other than default.
I know it's a quite silly question and the answer must have been written a zillion times here, but I swear I searched and got lost in similar-looking other-problems posts.
Thanks in advance!

---

### Post by yancek on 2014-10-20
These settings are not the same on every computer.  It will depend on the manufacturer if it an HP, Dell, Toshiba, etc. and also the motherboard manufacturer.  If you could post that kind of information someone might be able to point you in the right direction.  Also, clarify what you are trying to do.  Do you have a pre-installed windows 8 and are trying to boot some OS from a usb or something else?

---

### Post by Bucky Ball on 2014-10-20
To boot from USB, try hitting F12 after the manufacturers splash screen at boot. That should get you to a boot device selection (on most machines). You can also change the boot device in the BIOS. The keys to get there vary, but after manufacturer splash, common is 'del' or F2. Good luck.

---

### Post by stalkingwolf on 2014-10-21
I have seen all of the following on different machines.
F8 F10 F12 Del Esc  and as i recall one oddball F11

---

### Post by irv on 2014-10-21
What I had to do to boot from a USB was to insert the USB while in Win 8, Do a reboot while holding down the Shift key. It boots to a menu where you select boot from CD or USB, If the USB does not show in the menu, you have to do this twice. At least I had to do it twice. I think it's a bug in Win 8. I am writing this from memory seeing I don't use Win 8 anymore. I run just Ubuntu. By the way I have a Asus Q500A laptop.

EDIT: you might have to use this same (hold down Shift key) to boot into BIOS and turn off fast boot and secure boot to boot from USB. As I remember I had to do this.

---

### Post by cwmoser on 2014-10-21
> **irv said:**
> 
....
EDIT: you might have to use this same (hold down Shift key) to boot into BIOS and turn off fast boot and secure boot to boot from USB. As I remember I had to do this.

I second Irv.  This week I had to turn off Secure Boot in the BIOS in order to install Ubuntu 14.04 in a
laptop that had Windows 8 on it.  A friend of mine was so disgusted with Windows 8 that she told
me to install Ubuntu.  Second one this month.

Carl

---

