---
title: "No sound"
date: 2008-10-23
forum: New to Ubuntu
---

### Post by worlestone on 2008-10-23
I did have sound working on my PC, but since an update a few days ago I've no sound.  Speaker icon in top right shows a speaker with like a red warning/no entry type sign.  If I right click it and click on Open Volume Control I get the message:

No volume control GStreamer plugins and/or devices found.

I've searched and tried a few solutions, installing lots of 'alsa' stuff, but nothing works.

Could someone offer some advice please :-)

Thanks

Adrian

---

### Post by Sealbhach on 2008-10-23
What version of Ubuntu are you using?

Just take a skim through some of these results here...

[http://www.google.co.uk/search?hl=en&q=%22No+volume+control+GStreamer+plugins+and%2For+devices+found%22&btnG=Google+Search&meta=](http://www.google.co.uk/search?hl=en&q=%22No+volume+control+GStreamer+plugins+and%2For+devices+found%22&btnG=Google+Search&meta=)

They seem to suggest you may have to reinstsall a sound module.


.

---

### Post by worlestone on 2008-10-24
I'm using 8.04.  A few days ago I tried installing mythbuntu in Virtualbox to try out rather than dual boot.  The install of Mythbuntu didn't work and I was left with video card detection errors which I sorted out, but not sure now.  Sound might have gone at the same time.

The link I tried didn't work, I was not able to do:

sudo chmod 660 /dev/snd/*

came back with:

adrian@adrian-desktop:~$ sudo adduser $(who am i | cut -d" " -f 1) audio
[sudo] password for adrian: 
The user `adrian' is already a member of `audio'.
adrian@adrian-desktop:~$ sudo chmod 660 /dev/snd/*
chmod: cannot access `/dev/snd/*': No such file or directory
adrian@adrian-desktop:~$ 

I assume this directory should exist?

Help!

---

### Post by Sealbhach on 2008-10-24
Other people reporting the same problem here. I think it may have been a kernel updater which caused it.

[http://ubuntuforums.org/showthread.php?p=6017231](http://ubuntuforums.org/showthread.php?p=6017231)

What happens if you try alsamixer?

```
alsamixer
```

Also, what does 

```
uname -a
```

give?

Also, this thread [here]("https://answers.launchpad.net/ubuntu/+question/27909") recommends trying this:

```
sudo apt-get update
sudo apt-get upgrade
sudo apt-get install linux-ubuntu-modules-$(uname -r)
```

.

---

### Post by worlestone on 2008-10-25
Results are:

adrian@adrian-desktop:~$ alsamixer

alsamixer: function snd_ctl_open failed for default: No such file or directory
adrian@adrian-desktop:~$ 

adrian@adrian-desktop:~$ uname -a
Linux adrian-desktop 2.6.24-21-386 #1 Mon Aug 25 16:58:26 UTC 2008 i686 GNU/Linux
adrian@adrian-desktop:~$ 

Finally...

adrian@adrian-desktop:~$ sudo apt-get update
[sudo] password for adrian: 
Ign cdrom://Mythbuntu 8.04.1 080705 i386 hardy Release.gpg
Ign cdrom://Mythbuntu 8.04.1 080705 i386 hardy/main Translation-en_GB       
Ign cdrom://Mythbuntu 8.04.1 080705 i386 hardy/restricted Translation-en_GB 
Ign cdrom://Mythbuntu 8.04.1 080705 i386 hardy/universe Translation-en_GB    
Ign cdrom://Mythbuntu 8.04.1 080705 i386 hardy Release                       
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy Release.gpg                           
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy/main Translation-en_GB                
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy/restricted Translation-en_GB
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy/universe Translation-en_GB
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy/multiverse Translation-en_GB
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-updates Release.gpg   
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-updates/main Translation-en_GB
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-updates/restricted Translation-en_GB 
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-updates/universe Translation-en_GB   
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-updates/multiverse Translation-en_GB 
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy Release                              
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-updates Release              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release.gpg           
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Translation-en_GB
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Translation-en_GB
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Translation-en_GB
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Translation-en_GB
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy/main Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy/restricted Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy/main Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy/restricted Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy/universe Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy/multiverse Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy/multiverse Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-updates/main Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-updates/restricted Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-updates/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-updates/restricted Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-updates/universe Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-updates/universe Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-updates/multiverse Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-updates/multiverse Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Sources
Reading package lists... Done
adrian@adrian-desktop:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
adrian@adrian-desktop:~$ sudo apt-get install linux-ubuntu-modules-$(uname -r)
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libqt4-core libxalan110 libqt4-gui libmikmod2 alsaplayer-gtk libxerces27
Use 'apt-get autoremove' to remove them.
The following NEW packages will be installed
  linux-ubuntu-modules-2.6.24-21-386
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 5412kB of archives.
After this operation, 16.9MB of additional disk space will be used.
Get: 1 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-updates/main linux-ubuntu-modules-2.6.24-21-386 2.6.24-21.32 [5412kB]
Fetched 5412kB in 6s (808kB/s)                                                 
Selecting previously deselected package linux-ubuntu-modules-2.6.24-21-386.
(Reading database ... 153122 files and directories currently installed.)
Unpacking linux-ubuntu-modules-2.6.24-21-386 (from .../linux-ubuntu-modules-2.6.24-21-386_2.6.24-21.32_i386.deb) ...
Setting up linux-ubuntu-modules-2.6.24-21-386 (2.6.24-21.32) ...
update-initramfs: Generating /boot/initrd.img-2.6.24-21-386

adrian@adrian-desktop:~$ 

Thanks for the help, but still no sound!

---

### Post by Sealbhach on 2008-10-25
OK, well I guess the most thorough way of checking this out is to go through the sound troubleshooting guide.

[http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)

It could be the soundcard, or the modules or it could be the plugins so that guide will narrow down where the problem is.


.

---

