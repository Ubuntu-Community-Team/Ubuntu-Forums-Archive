---
title: "bypass grub bootloader"
date: 2011-10-29
forum: New to Ubuntu
---

### Post by fattyz on 2011-10-29
I got a blank screen on my acer lappy after an update in 11.04 so I tried going up to 11.01 but it hardly runs for whatever reason.  I want to reinstall 11.04 from a usb stick but can not get past bootloader.

Please help!

FattyZ

---

### Post by mike555 on 2011-10-29
Are you pushing the F12 button during startup? or whatever key yours uses to give you a boot option?

---

### Post by fattyz on 2011-11-05
yes it goes wherever I want but then it just goes bak to the bootloader I can not make it boot off a cd or usb drive HELP

Ps I have a working usb boot and dvd boot but I cant go bak to 10.04 please anybody get me out of this!  aLL my stuff is on that laptop and I have no access to any of it

Yours,  FattyZ

---

### Post by mike555 on 2011-11-05
What graphics do you have ?  you might need to set grub for "nomodeset "  until you install it and load drivers.

---

### Post by fattyz on 2011-11-06
Isn't there just a way to go back by booting off my usb?  I have no desire to mess around with this thing, I'll uprade when they work these BUGS out.  Any way to bypass grub boot loader ???  Anyone!!!!  I'm desperate.

Thanks FattyZ

---

### Post by Basher101 on 2011-11-06
change the bootorder in your BIOS so your USB boots first. This way GRUB wont load

---

### Post by fattyz on 2011-11-06
> **Basher101 said:**
> change the bootorder in your BIOS so your USB boots first. This way GRUB wont load

This will not work and I don't know why, it only gives me the option of the boot loader. CD or USB will not boot even when boot order is changed in the BIOS . I am up and running now.  By going back through previous versions I found a 11.1 that starts and will not go to black screen.  I dont know why it thinks 11.1 is a previous version but it beats the blank screen.

I,d still like to switch back, Any advice appreciated.

FaTTYz

Well, up and running if you consider it won't take my WEP key so I have no internet on that box, PLEASE someone get me back to KANSAS!

---

### Post by mcduck on 2011-11-06
> **fattyz said:**
> Isn't there just a way to go back by booting off my usb?  I have no desire to mess around with this thing, I'll uprade when they work these BUGS out.  Any way to bypass grub boot loader ???  Anyone!!!!  I'm desperate.

Thanks FattyZ

You will not need to "bypass the bootloader" to boot from USB drive, and actually doing such thing wouldn't even help you at all.

The boot device selection happens *before* the boot loader runs. And it's handled by your computer's BIOS, so you'll either need to change your boot device order in BIOS settings, or access the boot selection menu immediately after powering on your system.

If either one of these methods fails to boot your USB drive, make *absolutely sure* your drive is prepared correctly and is bootable. The only reasons for such problem would be either wrong BIOS settings or not having a proper bootable drive.

---

### Post by mike555 on 2011-11-06
You might try a different loader like one on a cd ,one that will give you an option to boot a usb ....... like ;
  [http://www.plop.at/en/bootmanager.html](http://www.plop.at/en/bootmanager.html)     ... at least to try.

---

### Post by fattyz on 2011-11-06
Thanks I will, it is kind of strange it wont boot, it also gives me some scary errors but...though I booted with a 10.4 usb sitck it put me back into 11.10.  Running again.  I figure from there I have a better chance.

I dont know why the boot sequence wont work but it wont.  The USB drive or cd are set up correctly and the machine should be booting from there but, it wont.

I've had enough for today but I'll keep you posted, I can't be the only one with this going on.

thank you

Fattyz

---

### Post by fattyz on 2011-11-06
Thank God for winblows.   THings got worse as the day went on and now I have 11.01 running but can not connect it to the wireless network.  Well, I can run winblows on that as well in a pinch but would prefer my old (functional) versions of ubuntu back.  Don't get me wrong, I'm around long enough to know we all get stuck in computer hell from time to time so don't mind my bitching, I just think they should have made and easier path for backwards migration is all.

CU Boyz on the other side

FattyZ

---

