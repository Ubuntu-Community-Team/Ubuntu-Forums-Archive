---
title: "how do i create a booatable windows 10 installation media with a pendrive in ubuntu 2"
date: 2020-06-02
forum: New to Ubuntu
---

### Post by asxadssd on 2020-06-02
[RIGHT][COLOR=#000000]how do i create a booatable windows 10 installation media with a pendrive in ubuntu 20.04?[/COLOR][/RIGHT]

---

### Post by SeijiSensei on 2020-06-02
See if usb-creator-gtk (or usb-creator-kde if you're on that desktop) works.  I think I used Rufus on Windows to make mine, but I don't recall at the moment.

---

### Post by CelticWarrior on 2020-06-02
> **SeijiSensei said:**
> See if usb-creator-gtk (or usb-creator-kde if you're on that desktop) works.

It doesn't, neither of them.
WoeUSB works but up to until recently couldn't be installed in 20.04 due to dependencies (it's fine in 19.10 and earlier).

---

### Post by peb-cak on 2020-06-02
There is also this one:
[URL="https://github.com/ValdikSS/windows2usb"]
https://github.com/ValdikSS/windows2usb[/URL]

It comes as an appimage which is run in terminal. I haven't used it myself so I cannot guarantee if it is up to the task.

---

### Post by CelticWarrior on 2020-06-02
> **peb-cak said:**
> There is also this one:
[URL="https://github.com/ValdikSS/windows2usb"]
https://github.com/ValdikSS/windows2usb[/URL]

It comes as an appimage which is run in terminal. I haven't used it myself so I cannot guarantee if it is up to the task.

New to me. 

> 
[LIST]
[*]Supports custom Windows ISOs with install.wim > 4GiB
[/LIST]

is promising. Not supporting it is the reason why most other tools don't work.

---

### Post by peb-cak on 2020-06-02
Yes, looks promising. I haven't had any opprtunity to try it out yet. Simply the need of installing Windows hasn't been there. Would be nice if OP wants to give it a shot.

---

### Post by rbmorse on 2020-06-02
Something has changed in the Windows .iso that causes one of the data partitions on the Flash media to be larger than 4Gb. Since it's formatted FAT, that obviously causes a problem. Go Microsoft! Never change. 

I installed Win 10 last weekend as a second O/S on one of my Linux machines (this one, in fact) and had to resort to creating the Win installer on a double layer optical disc.  PITA.  There's a work around for flash devices, but I didn't see it until after the installation was completed and forgot to note where it was at the time. 

an aside: I know the conventional wisdom says we're supposed to install Windows first on a multiboot system, but since I was planning to redo the Ubuntu installation anyway I thought I'd just give it go and see what was required to fix the damage.  This is a desktop class machine with Nvidia GPU.  

The Windows Ten version 2004 installer surprised me.  It detected and used the ESP created by Ubuntu and didn't overwrite the existing GRUB (or rEFInd) already present in the ESP.  It created new partitions for Windows reserved and the Windows system from empty space on the drive where  directed (now nvme0n1p3 and p4).  It did not otherwise mess with Ubuntu.  All I had to do was add Windows to the GRUB menu with update-grub (and then go to work on decrufting and configuring Windows...that's still a big PITA). 

Worked just like a good Linux installer.  I was expecting all sorts of shenanigans and getting re-accquainted with boot repair, but that turned out to be unnecessary.

---

### Post by rbmorse on 2020-06-02
I found the site with the instructions on creating a working flash media installer for Windows 10:

[https://win10.guru/usb-install-media-with-larger-than-4gb-wim-file/](https://win10.guru/usb-install-media-with-larger-than-4gb-wim-file/)

---

### Post by C.S.Cameron on 2020-06-02
**Mkusb-plug** should work see post 948, bottom, here: [https://ubuntuforums.org/showthread.php?t=1958073&page=95&p=13961108#post13961108](https://ubuntuforums.org/showthread.php?t=1958073&page=95&p=13961108#post13961108)
(I have not tested the Windows installer yet).

---

### Post by sudodus on 2020-06-03
- The new version of **mkusb-dus** (still in the unstable PPA, ppa:mkusb/unstable) and

- the current version of **mkusb-plug** (in the stable PPA, ppa:mkusb/ppa)

can create installer drives for Windows 10 with a huge install.wim file. They work in Ubuntu 20.04 LTS and also in the developing version Groovy Gorilla.

- [mkusb-dus alias version 12](https://help.ubuntu.com/community/mkusb/) works in all current versions of Ubuntu.

- [mkusb-plug](https://help.ubuntu.com/community/mkusb/plug) works in Ubuntu 18.04 LTS and newer versions. You cannot install it from PPA into 16.04 LTS, but can install it from tarball (into 16.04 LTS and newer versions).

---

### Post by rbmorse on 2020-06-03
FWIW, mkusb-dus version 12 running on 20.04 wouldn't make a usable Windows install flash device for me (wim.install truncated) , but I just tried mkusb-plug and that worked fine.

---

### Post by sudodus on 2020-06-03
@rbmorse,

The version in mkusb's stable PPA has only an old version to create a Windows installer, but the version in the unstable PPA has an additional new submenu: You can choose between the old version, which might be necessary with old versions of Windows and in 32-bit versions of Ubuntu, and the new version with the same engine, mkusb-tow, as in mkusb-plug, so it *should* work with the new Windows 10 iso files.

Please check which version of mkusb-dus that you have installed:

```

dus -v

```
You need the current version of mkusb-dus from the unstable PPA for this new tool, mkusb-tow:
```

dus 12.5.7

```

If it does not work for you in dus 12.5.7, please help me debug it.

But if you use the stable PPA, and do not want to change to the unstable one because you want stability, it is OK. After testing by me and some other people and maybe some debugging, you will get this new tool into the stable PPA and mkusb-dus.

---

