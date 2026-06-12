---
title: "Can't boot into 11.10, dual boot with windows 7"
date: 2011-10-16
forum: New to Ubuntu
---

### Post by pishboy on 2011-10-16
I recently got a copy of ubuntu 11.10 and extracted the iso file into my usb and boot up from it. I ran into problems with grub (i had a previous installation of ubuntu 10 and removed it prior to installation using windows 7), used the windows 7 installation disk and fixed the bootloader of windows using the command prompt:
```
bootrec /fixmbr
```
restarted and checked if windows was working fine. I then plugged in my USB and proceeded to install ubuntu, selecting "Install ubuntu alongside Windows" (i had free space because of my previous installation) the isntall worked out nice and asked me to reboot. I removed my USB, pressed enter but after the BIOS screen (i'm on an ASROCK mobo) windows booted up without GRUB appearing.
Am i missing something here? or can i install GRUB from the live USB? Getting rid of Windows 7 is not an option because my cousins also use this computer (shared computer) and their notion of "Computer" is "A device running Windows" (which makes me think what would their reaction be once windows 8 is out)
Also, i'm still getting used to Ubuntu and i'm worried some programs won't work with ubuntu.
Thanks in advance!

---

### Post by abnordude on 2011-10-16
If you want to install GRUB, why dont you give boot repair disc, a try.

[http://sourceforge.net/p/boot-repair-cd/home/Home/](http://sourceforge.net/p/boot-repair-cd/home/Home/)

Try this..
Hope it works.

---

### Post by pishboy on 2011-10-16
> **abnordude said:**
> If you want to install GRUB, why dont you give boot repair disc, a try.

[http://sourceforge.net/p/boot-repair-cd/home/Home/](http://sourceforge.net/p/boot-repair-cd/home/Home/)

Try this..
Hope it works.

I'll try it tomorrow ( i'm in UTC+08 ) and i don't have much time to download it (it'll take me 1 hour to download, blame my very super fast internet connection)

---

### Post by garvinrick4 on 2011-10-16
Yes you can.
run in terminal or Live Cd (install cd using Try Ubuntu)
```
sudo fdisk -l
```(lowercase L)
Pick out your linux install and use that sda#
I will use sda5 for this, y[COLOR=Red]ou use your own:[/COLOR]
```
sudo mount /dev/sda5 /mnt
``````
sudo grub-install --root-directory=/mnt /dev/sda
``````
sudo umount /mnt
``````
sudo reboot
```Boot into Ubuntu
```
sudo update-grub
```

---

