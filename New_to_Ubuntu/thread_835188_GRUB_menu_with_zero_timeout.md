---
title: "GRUB menu with zero timeout"
date: 2008-06-20
forum: New to Ubuntu
---

### Post by ampersand38 on 2008-06-20
Hi all.

I am dual booting Ubuntu 8.04 with Vista.
I have set GRUB to default to Vista with zero (0) timeout under the impression that i could pause the boot process by pressing Escape, and then choose Ubuntu when I need it.

Now, however, I am unable to select ubuntu as the menu is only shown for a fleeting moment before Vista is booted.

Is there anyway to be able to select the OS to boot with menu timeout set to zero?

Thanks.

---

### Post by Joeb454 on 2008-06-20
Just keep hitting Escape while booting :)

---

### Post by drs305 on 2008-06-20
After you get it started, you might want to change your menu display to 1 second for future boots. If so, here is a link to how to set it up:
[HOWTO: Grub Menu Kernel Display Options]("http://ubuntuforums.org/showthread.php?t=818177")

---

### Post by ampersand38 on 2008-06-20
Hmm. it seems there is some trick to this :)
if i press escape during POST, the BIOS gives me a menu to choose boot device.
if i wait until i see "Grub 1.5 ..." and then press escape, i get windows boot manager, with vista as the only option. 
and, if i press escape repeatedly, GRUB and windows boot manager both flash by and the system reboots.
how strange...

EDIT:
drs305: I am considering that too. I will try it.

---

### Post by GuitarRocker2562 on 2008-06-20
Guessing that ubuntu is on the top of your list, just press up repeadily for the time you see loading stage 1.5 until hopefully ubuntu

---

### Post by joshedmonds on 2008-06-20
Boot using an Ubuntu LiveCD.

Edit the menu.lst file at /boot/grub on the drive grub is installed to:

```
sudo gedit /boot/grub/menu.lst
```

Give yourself a couple of seconds to change your selection:

```
timeout 3
```

Save the file, reboot (making sure you remove the liveCD) and try again. It is probably a good idea to check your menu.lst while you are editing it to make sure you have an appropriate Ubuntu boot menu item, something like:

```
title		Ubuntu 8.04
root		(hd0,1)
kernel		/vmlinuz root=/dev/sda2 ro quiet splash
initrd		/initrd.img
quiet
```

---

### Post by ampersand38 on 2008-06-20
Problem Solved

The actual path to menu.lst from the Live Cd is

```
/media/disk/boot/grub/menu.lst
```

after getting there, sudo gedit worked fine :D

---

### Post by lavinog on 2008-06-20
you could have used a windows driver to access your ext3 drives also...comes in handy when you are dual booting...one that i use is ifsdrives but i have only used this on xp...don't know how well it works for vista.
this will save you the trouble of having to find/burn an ubuntu cd if not readily available

---

### Post by Duck2006 on 2008-06-20
In your Synaptic Package Manager load startup-manager, it makes editing your menu.lst a lot easyer.

---

### Post by lavinog on 2008-06-20
> **Duck2006 said:**
> In your Synaptic Package Manager load startup-manager, it makes editing your menu.lst a lot easyer.

only works if you can boot to ubuntu though

---

### Post by Duck2006 on 2008-06-20
Ok then the best bet would be is to use EasyBCD boot loader. As it runs from the windoze boot loader.

[http://neosmart.net/dl.php?id=1](http://neosmart.net/dl.php?id=1)

---

### Post by lavinog on 2008-06-20
> **Duck2006 said:**
> Ok then the best bet would be is to use EasyBCD boot loader. As it runs from the windoze boot loader.

[http://neosmart.net/dl.php?id=1](http://neosmart.net/dl.php?id=1)

The point was all the op needed was to edit the menu.lst file to change the delay from 0 to some number.
The EasyBCD bootloader setup looks like it will be alot more work to setup for an existing linux setup.


Looking at the site posted:
[http://neosmart.net/wiki/display/EBCD/Linux]("http://neosmart.net/wiki/display/EBCD/Linux")
> NeoGrub is NeoSmart Technologies' implementation of the open-source GRUB bootloader (ported over to Windows by the Grub4Dos team)
...
[http://neosmart.net/wiki/display/EBCD/NeoGrub]("http://neosmart.net/wiki/display/EBCD/NeoGrub")
> With EasyBCD 1.7, NeoGrub was completely overhauled, with full-quality standards-compliant code and behavior, with support for more platforms and filesystems - and is several times more powerful than the original. To date, NeoGrub has played a major role in getting non-compliant, buggy, and out-dated operating systems to boot with Windows Vista - along with a number of other nifty tricks that couldn't be done otherwise. It even lets you load Windows in ways that the Vista bootloader makes quite impossible!

NeoGrub is made possible thanks to the efforts of the Grub4Dos project and their work on a Windows-compatible GRUB bootloader.
Is the author violating the GPL?

---

### Post by Duck2006 on 2008-06-20
No it,s not. Once you have it installed it will run well. I use wingrub and have no problems with it.

---

