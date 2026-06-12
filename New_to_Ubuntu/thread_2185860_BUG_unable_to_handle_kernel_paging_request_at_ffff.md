---
title: "BUG: unable to handle kernel paging request at ffffffffa0543020"
date: 2013-11-04
forum: New to Ubuntu
---

### Post by guadaatenea on 2013-11-04
Asus x201e notebook
It came with Windows 8
2gb-RAM
Celeron processor
No CD/DVD drive -I'm using a bootable USB
I'm installing 12.04.3 desktop 64bits



I managed to get it to boot from USB, opened the trial version -it went OK-, clicked the installing icon, selected language and got stuck on this screen forever:

[IMG]https://dl.dropboxusercontent.com/u/85050466/P1030661.JPG[/IMG]


Eventually I felt uneasy, restarted it and saw old Windows 8 again. I'm starting to feel Windows 8 startup screen as if it were some weird version of Groundhog Day's radio alarm clock...

---

### Post by sandyd on 2013-11-04
That looks like [https://bugs.launchpad.net/ubuntu/+source/linux-lts-raring/+bug/1247712](https://bugs.launchpad.net/ubuntu/+source/linux-lts-raring/+bug/1247712)

---

### Post by guadaatenea on 2013-11-05
stil, it got stuck 15' there and wouldn't launch installation, is there a chance I might fix it otherwise?

---

### Post by prantlf-c on 2013-12-15
I got this error when I was trying to install the 12.04.3 LTS 64-bit on Dell Latitude E6430 from USB, which I prepared with the [UNetbootin]("http://unetbootin.sourceforge.net/") (in Windows).  At last I created the installation USB with the [Universal USB Installer]("http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/") and the installation succeeded.

---

