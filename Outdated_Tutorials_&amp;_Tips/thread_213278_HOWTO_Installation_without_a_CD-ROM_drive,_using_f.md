---
title: "HOWTO: Installation without a CD-ROM drive, using floppies"
date: 2006-07-11
forum: Outdated Tutorials &amp; Tips
---

### Post by agger on 2006-07-11
I was [somewhat perplexed some time back]("http://www.ubuntuforums.org/showthread.php?t=203586&highlight=floppy") as to how I should install Ubuntu on an old PC we have with no CD-ROM drive. I have no DHCP server which could be used for a network boot.

So, I thought I had found the solution here, on the Wiki:

[https://help.ubuntu.com/community/Installation/WithFloppies](https://help.ubuntu.com/community/Installation/WithFloppies)

Alas, it didn't really work.

**What they suggest you do is: **

1) Get hold of boot floppies for installing Debian Sarge - get them from the [Debian archive]("http://ftp.egr.msu.edu/debian/dists/sarge/main/installer-i386/current//images/floppy/").
2) Start installing, and bail out to the TTY before the real installation starts, right after the Debian installer has completed partitioning the disk.
3) get hold of something called *debootstrap* from an Ubuntu archive and let this program download the system.

Unfortunately, i could **not** get this to work.

**What did work  for me was**:

1) Get hold of boot floppies for installing Debian Sarge - get them from the [Debian archive]("http://ftp.egr.msu.edu/debian/dists/sarge/main/installer-i386/current//images/floppy/").

2) Insert the boot disk, hit <enter> at the prompt and start installing. Just let the Debian installer do its work until the time when you get to reboot and set up users. When prompted for additional packages to install, do NOT enter any, install ONLY Debian base system.

3) When you have set up users and you can log in to your Debian base system, login as root and edit the [FONT="Courier New"]/etc/apt/sources.list[/FONT] file.

Replace whatever's there with this:
```

deb http://archive.ubuntu.com/ubuntu dapper main restricted
deb http://security.ubuntu.com/ubuntu dapper-security main restricted
deb http://archive.ubuntu.com/ubuntu dapper-updates main restricted

```

In the comand prompt, now write the following commands
```

apt-get update

```
(wait for completion)
```

apt-get upgrade

```
(wait)
```

apt-get dist-update

```

Now, get the newest kernel:
```

apt-get install linux-686 

```
(assuming you're using a Pentium II or upwards).
Your Debian Sarge base installation has now been converted into an Ubuntu base installation.

Reboot, boot into the newest kernel (once more as root), and
do a 
```

apt-get install ubuntu-desktop

```
If you want Xubuntu or Kubuntu instead, write 
```
apt-get install kubuntu-desktop
``` 
or 
```
apt-get install xubuntu-desktop
``` instead.

Now, the system will begin downloading close to one Gb of files to your harddisk, and will set up GDM to autodetect everything to log you safely into GNOME - just as if you installed from a CD.

Everything in the Debian base system you started installing has now been replaced by the corresponding Ubuntu version.

**Pitfalls**:
If the Debian installer gives you a 2.4 kernel, don't try to log in to it if you wish to run Gnome/KDE or other X window systems: Xorg won't run on it. Make sure you downloaded the 2.6 kernel before installing (x/k)ubuntu-desktop. (This took me quite some time to figure out - I don't know if there are any other pitfalls).

Maybe some time an "official" floppy/get everything from the Network installation procedure for Ubuntu would be in order so we don't have to use this Debian Sarge workaround?

Anyway, my system is now up and running and there's a screenshot of it [in my blog]("http://www.modspil.dk/billeder/linux_i_juli__xubuntu_6_06.html") :-)

---

### Post by nkhansen on 2006-07-11
Great solution, thanks. Maybe I WILL buy that Lenovo Subnote without a optical drive.

---

### Post by Shafiq on 2006-07-29
Wow, that was priceless. This is exactly what I needed to get xubuntu onto my C1 vaio.

Thanks!!

---

