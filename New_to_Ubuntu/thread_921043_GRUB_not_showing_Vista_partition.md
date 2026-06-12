---
title: "GRUB not showing Vista partition"
date: 2008-09-15
forum: New to Ubuntu
---

### Post by Skimbleshanks on 2008-09-15
So when you've picked yourself up off the floor and got the hysterics under control...

Having dipped my toe by installing Xubuntu Dapper on a desktop PC I felt confident enough to install same on a Compaq Presario laptop.

Can anybody help? GRUB is not showing the Windows Mojave ... er, I mean ***Vista*** partition when I start. I selected less than half the available space when I set up the partition, so is there a way to get it back?

---

### Post by modmadmike on 2008-09-15
You have to edit 2 things: etc fstab  if you havent mounted your windows partition to a directory such as /windows, Then you have to edit the /bott/grub/menu.lst to add your windows install

---

### Post by shoot2kill on 2008-09-15
what are the results of...

```

fdisk -l

```
and
```

gedit /boot/grub/menu.lst

```

---

### Post by modmadmike on 2008-09-15
here's what my windows entry in the menu.lst file title		
```
Windows Vista/Longhorn (loader)
root		(hd2,0)
savedefault
chainloader	+1
```

---

### Post by pbotros1234 on 2008-09-15
/boot/grub/menu.lst, not /bott/grub/menu.lst, just to avoid any confusion

And if you just do:
```
sudo update-grub
```

Haven't tried this myself, but I think it also might work.

---

### Post by modmadmike on 2008-09-15
> **pbotros1234 said:**
> /boot/grub/menu.lst, not /bott/grub/menu.lst, just to avoid any confusion

And if you just do:
```
sudo update-grub
```

Haven't tried this myself, but I think it also might work.

yea I wasn't checking my spelling lol

---

### Post by Skimbleshanks on 2008-09-16
Thanks to all for your recommendations. As it turns out, I have a whole lot more issues to resolve, including, trackpad not working (and isn't F2 supposed to launch the terminal? no joy there either). I think it may be due to no ACPI...

I tried reinstalling in case I had mucked up the partitioning stage, and reboot resulted in the following messages:

MP-BIOS bug: 8254 timer not connected to IO-APIC
Kernel panic - not syncing: IO-APIC + timer doesn't work!

So I would like to thank each of you for attempting to help me. I'm sorry I can't offer more than words, but your willingness to share your knowledge and time is very much appreciated.

---

### Post by modmadmike on 2008-09-16
> **Skimbleshanks said:**
> Thanks to all for your recommendations. As it turns out, I have a whole lot more issues to resolve, including, trackpad not working (and isn't F2 supposed to launch the terminal? no joy there either). I think it may be due to no ACPI...

I tried reinstalling in case I had mucked up the partitioning stage, and reboot resulted in the following messages:

MP-BIOS bug: 8254 timer not connected to IO-APIC
Kernel panic - not syncing: IO-APIC + timer doesn't work!

So I would like to thank each of you for attempting to help me. I'm sorry I can't offer more than words, but your willingness to share your knowledge and time is very much appreciated.
 F2 is not normally mapped to launch terminal I use insert, to set a hot key just go to System>Preferences>Keyboard Shortcuts. As for the the track pad I don't know because iv'e never had this problem If its a Synaptics Touchpad then you usually don't need to install the driver, and Elantech (as with the Eeepc 901-1000) you need a hack, or elantech's driver both can be found by Googling. As for anything else, I have never heard of it so i don't know.

---

