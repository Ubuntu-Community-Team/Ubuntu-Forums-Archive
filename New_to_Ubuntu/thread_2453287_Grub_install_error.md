---
title: "Grub install error"
date: 2020-11-06
forum: New to Ubuntu
---

### Post by goddude on 2020-11-06
I'm trying to install ubuntu 20.4 in my external HDD I've done everything said on the internet. I have made partition with gparted with a 4gb swap(I have 4gb ram) 100mb fat32 efi and a ext4 part with 150gb. Still everytime i try to install it shows grub-install dev/sdac error fatal. Then restart option. Can anyone please help

---

### Post by tea for one on 2020-11-06
> **goddude said:**
> I've done everything said on the internet.

You must have spent many hours reading and following the wide expanse of the internet ;)

Anyway, if you want to use an external device (albeit HDD, USB, SDD) for Ubuntu, here is my suggestion:-

[COLOR="#0000FF"]Disable,[/COLOR] [COLOR="#FF0000"]de-activate,[/COLOR] [COLOR="#4B0082"]remove[/COLOR] your internal drive(s) - either via UEFI set up pages or physically.
Boot into your live Ubuntu session.
Open gparted and make your external device into GPT (partition table).
Install Ubuntu to your external device - it will be the only device available as you have already isolated all other options.
Grub will only find the external device.

Do **not** activate your internal drives.
Reboot and test.

---

