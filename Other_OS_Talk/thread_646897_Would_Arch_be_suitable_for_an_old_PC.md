---
title: "Would Arch be suitable for an old PC?"
date: 2007-12-21
forum: Other OS Talk
---

### Post by TheOrangePeanut on 2007-12-21
I am at my parents house for Christmas break and I have some time to kill.  

The computer I use here is a 450 mhz P3 with 384 MB of ram and a Radeon 7000 video card.  Obviously, it is a few years old.  I'm currently running Xubuntu 6.06, but I'm interested in a distro that is a little faster.

Would Arch be a good choice?  I've only installed Ubuntu derivative distros, so installing Arch would def be a learning experience.  If I messed up too bad, I could always just reinstall Xubuntu; it doesn't take but about an hour.

Sound like a good idea?  I was thinking I'd install Arch with Fluxbox WM, but what file browser should I use?  Is there anything else I need to know besides what the Arch docs will tell me?

---

### Post by Dimitriid on 2007-12-21
Arch is indeed very fast. I prefer openbox to fluxbox but in both cases I still use Thunar as a file manager: its not that light but it does has some nice features build in.

There are other options however, check the openbox wiki ( all the file managers should apply to fluxbox easily )

[http://wiki.archlinux.org/index.php/Openbox#File_managers](http://wiki.archlinux.org/index.php/Openbox#File_managers)

---

### Post by Rumor on 2007-12-21
I have an older computer at my office that has Arch on it. it is an old P2/350(?) and it runs fine. It is quite snappy for such an old machine.

I like pcman as a file manager. It is quite lightweight and nicely featured. [http://pcmanfm.sourceforge.net/](http://pcmanfm.sourceforge.net/)

---

### Post by jseiser on 2007-12-21
are would run fine.  
evilwm, xmonad, awesome, dwm rapoison would all work fine as a WM
rtorrent for torrents
mc for files
leafpad / nano / vim for text
elinks / dillo / kazehakase for web browsing
mutt for email
mpd + ncmpc for music
Sakura / for terminal

That machine would be beastin on that setup.

---

### Post by mips on 2007-12-22
Someone gave me a Dell Latitude C600/C500 laptop today to see if I could turn it into a useable machine again.

Specs:
PIII  850MHz
256MB RAM
10GB HD
ATI card of sorts
CD-ROM Faulty, cant' read or boot media, keeps on telling me to insert disc.

I'm thinking of putting arch + kdemod on here. Would this be useable?

How do I install an OS if the CD-ROM is faulty. No option to boot from USB in BIOS.

---

### Post by D-EJ915 on 2007-12-23
> **mips said:**
> Someone gave me a Dell Latitude C600/C500 laptop today to see if I could turn it into a useable machine again.

Specs:
PIII  850MHz
256MB RAM
10GB HD
ATI card of sorts
CD-ROM Faulty, cant' read or boot media, keeps on telling me to insert disc.

I'm thinking of putting arch + kdemod on here. Would this be useable?

How do I install an OS if the CD-ROM is faulty. No option to boot from USB in BIOS.
850 would actually be kinda snappy, hard drive is definitely the limiting factor there, it's probably pretty slow.

---

### Post by Dimitriid on 2007-12-23
You can't trust either hdd or optical, your best bet is that this is able to either boot to USB or has a working floppy, in which case you could easily use puppy even if hdd and optical are busted.

---

### Post by K.Mandla on 2007-12-24
> **mips said:**
> How do I install an OS if the CD-ROM is faulty. No option to boot from USB in BIOS.
Supposedly (I've never gotten it to work) you can boot grub to an ISO image, so if you can copy the ISO onto a spare partition on the drive, you should be able to boot to it and install to another partition. 

Again, I've never gotten it to work, but I've never tried very hard either.
> **D-EJ915 said:**
> 850 would actually be kinda snappy, hard drive is definitely the limiting factor there, it's probably pretty slow.
It might be slow, but it might be okay. Both WD and Seagate made 7200rpm 10Gb hard drives that came stock in business-grade desktop machines for Dell and Gateway. I don't know if the laptop line would ever have one but you could check. I used to keep two or three of the WD Caviar Experts on hand because they were quick to blank and quick to boot, and I never need much system space -- that's what USB external drives are for! :biggrin:
> **Dimitriid said:**
> You can't trust either hdd or optical, your best bet is that this is able to either boot to USB or has a working floppy, in which case you could easily use puppy even if hdd and optical are busted.
Would that Puppy boot floppy work with any bootable USB key, or is it wired to run Puppy only? I know there's a Slax boot CD that supposedly will run anything USB that's bootable (even if it's not Slax), but I don't know if there's a floppy version. Probably not.

---

### Post by chris4585 on 2007-12-28
i'd go with fluxbuntu bu arch would be just as good if not better, personally i wanna try and build my own from ubuntu scratch, but you might not want to take all your time into making that machin perfect

---

