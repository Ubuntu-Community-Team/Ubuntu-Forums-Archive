---
title: "Erasing disk and installing Ubunutu"
date: 2018-05-18
forum: New to Ubuntu
---

### Post by gdawgs47 on 2018-05-18
I'm trying to erase disk and install ubuntu 18.04 LTS on my dell laptop.  Before, it was saying root file system could not be found when trying  "erase disk and install Ubuntu". I tried messing around with partition  size but now  nothing comes up. Windows 10 was partitioned but I'm not  sure if I deleted it. The install was crashing a few seconds into each  install. 

[https://imgur.com/a/jQ1KjgT](https://imgur.com/a/jQ1KjgT)

---

### Post by oldfred on 2018-05-18
Post this to see if you have any partitions:
sudo parted -l

What model system? What video card?
What version of Windows and was it UEFI or BIOS?
And are you installing in UEFI or BIOS boot mode?

---

### Post by kerry_s on 2018-05-19
sometimes you have to reboot & try again.

---

### Post by gdawgs47 on 2018-05-19
i used ubuntu 16.04 instead and it worked fine

---

### Post by oldrocker99 on 2018-05-19
> **gdawgs47 said:**
> i used ubuntu 16.04 instead and it worked fine

FWIW, Ubuntu 18.04 is out and solid as a rock. If you don't like GNOME, give Ubuntu MATE a try. It's lightweight, very configurable, in fact giving the user a choice including Redmond (Windows7), Cupertino (MacOS), and Mutiny, which recreates the much-loved and much-hated Unity desktop. No other distro gives you that much choice of desktop environments.

Burn it to a thumb drive, boot it up and see how you like it. For me, Ubuntu MATE is the best distro, hands down, of all the different distros I have tried. Most distros have a Welcome window, which typically tells about the OS, and includes links. Ubuntu MATE is the first distro to allow installation of drivers, as well as a wide, curated selection of software. It is excellent for the experienced power user, and the beginner. The few Linux fans I know use it, too.

You might well like it yourself.

---

