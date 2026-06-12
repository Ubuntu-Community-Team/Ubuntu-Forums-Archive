---
title: "upgrade from 11.04"
date: 2011-06-13
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by mick222 on 2011-06-13
I have messed up my system. I tried to upgrade from natty to oneric but got an error doc-base not installed. It will start but iat start up says something like cant start run/udev falling back to udev.
Should i just reinstall or is there a way to fix this.I tried to update via termional but got errors there to.

---

### Post by Harry33 on 2011-06-13
> **mick222 said:**
> I have messed up my system. I tried to upgrade from natty to oneric but got an error doc-base not installed. It will start but iat start up says something like cant start run/udev falling back to udev.
Should i just reinstall or is there a way to fix this.I tried to update via termional but got errors there to.

The error message about /run/udev is not any mess you have, it is the erroneus configuration of udev ATM. We all Oneiric users get that. So no problem. It does not harm in anyt way.

---

### Post by fjgaude on 2011-06-13
Gosh, we deal with a lot of breakage with installing early Alpha OSs, eh?

---

### Post by mick222 on 2011-06-13
Thx but it starts in low graphics mode ,i know proprietary drivers dont normally work on development releases,and i have no system tab on top panel synaptic will not open as administrator. Could this be caused by the doc-base error which it said consider reporting.

---

### Post by Harry33 on 2011-06-13
> **mick222 said:**
> Thx but it starts in low graphics mode ,i know proprietary drivers dont normally work on development releases,and i have no system tab on top panel synaptic will not open as administrator. Could this be caused by the doc-base error which it said consider reporting.

Please give some more info on your setup.
- which graphics card do you use?
- which graphics driver and version are you using?
- which kernel version are you booting with?
- do you have any additional Personal Package Archives (PPA's) in your sources.list?
  check your /etc/apt/sources.list file. Is there a single word "Natty" left?

The package doc-base does not have anything to do with booting process.
You can install it (latest version is 0.10.1), if you wish, from the official repos.
It is used to generate the database of document metadata, which
other packages such as dwww, dhelp, doc-central, and rarian-compat
can use. Not a big deal anyway.

---

### Post by mick222 on 2011-06-13
> **Harry33 said:**
> Please give some more info on your setup.
- which graphics card do you use?
- which graphics driver and version are you using?
- which kernel version are you booting with?
- do you have any additional Personal Package Archives (PPA's) in your sources.list?
  check your /etc/apt/sources.list file. Is there a single word "Natty" left

I downloaded and reinstalled 11.10 and am using the current Nvidia drivers on a geforce 9400gt My Kernel is 2.6.39-3 and i have no PPA's installed.
Still cant get 3d unity but sort of expected that.

---

### Post by Harry33 on 2011-06-14
> **mick222 said:**
> I downloaded and reinstalled 11.10 and am using the current Nvidia drivers on a geforce 9400gt My Kernel is 2.6.39-3 and i have no PPA's installed.
Still cant get 3d unity but sort of expected that.

If you are using proprietary Nvidia drivers (nvidia-current), you should have a fast 3D desktop.

---

### Post by philinux on 2011-06-14
> **Harry33 said:**
> If you are using proprieatary Nvidia drivers (nvidia-current), you should have a fast 3D desktop.

I just installed nvidia-current and only unity2d will boot. I guess we'll have to wait for an update to get 3d.

System fully up to date. I'll chroot updates for now from natty.

Early days yet.

---

### Post by 23dornot23d on 2011-06-14
This thread explains better than I can what is needed to get the 3D on Nvidia drivers working at
this present time for the 3D ..... [LINK]("http://ubuntuforums.org/showthread.php?t=1781380")

It mentions upgrading the Graphics drivers ....

Maybe these will become available as standard in the repo's later though.

---

### Post by mick222 on 2011-06-14
thx I'll try installing xorg edgers it was the only way to get 3D drivers in Natty at this point to.

---

### Post by mick222 on 2011-06-14
installed xorg edgers but theme still looks terrible

---

### Post by Harry33 on 2011-06-14
> **mick222 said:**
> installed xorg edgers but theme still looks terrible

Do you have gnome-themes-standard installed?

---

### Post by mick222 on 2011-06-14
Thx Harry i just installed them. Just wanted to try out ocelot as i had a spare partition. Hope I'm not to annoying with the stupid questions.

---

