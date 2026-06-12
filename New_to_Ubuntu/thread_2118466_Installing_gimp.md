---
title: "Installing gimp"
date: 2013-02-21
forum: New to Ubuntu
---

### Post by DaveMcC on 2013-02-21
I have try ed to install gimp on this computer ubuntu ver 10 10 64bit

When I go via the Ubuntu software centre I get the error message

Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/pool/main/g/gimp/libgimp2.0_2.6.10-1ubuntu3_amd64.deb](http://gb.archive.ubuntu.com/ubuntu/pool/main/g/gimp/libgimp2.0_2.6.10-1ubuntu3_amd64.deb) 404  Not Found [IP: 91.189.92.201 80]
Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/pool/main/g/gimp/gimp-data_2.6.10-1ubuntu3_all.deb](http://gb.archive.ubuntu.com/ubuntu/pool/main/g/gimp/gimp-data_2.6.10-1ubuntu3_all.deb) 404  Not Found [IP: 91.189.92.201 80]
Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/pool/main/g/gimp/gimp_2.6.10-1ubuntu3_amd64.deb](http://gb.archive.ubuntu.com/ubuntu/pool/main/g/gimp/gimp_2.6.10-1ubuntu3_amd64.deb) 404  Not Found [IP: 91.189.92.201 80]


When I go to install via Terminal 
apt-get install gimp
E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
boss@Boss-desktop:~$ 

Help ?

Dave

---

### Post by kevdog on 2013-02-21
This usually means another process is using apt-get.

---

### Post by PowerBarry43 on 2013-02-21
Hi

I don't know about why you're getting 404 errors from the software centre but the terminal error is an easy one where you see:

```
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
```

that is ubuntu politely telling you that you don't have permission to install stuff. This is easily avoided by running your command with 'sudo' that's Super User DO so more or less saying run what follows as admin.

just run:

```
sudo apt-get install gimp
```

and if that doesn't work post back the output here ;)

Hope this helps!

Barry

---

### Post by DaveMcC on 2013-02-21
Thanks Barry,
I thought it was going to work, then at the end,  I have put a line in to make it easy to see the failing

(here is the terminal window)

boss@Boss-desktop:~$ sudo apt-get install gimp
[sudo] password for boss: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libproc-processtable-perl unpaper tesseract-ocr libgraphicsmagick3
  libio-stringy-perl libreadonly-perl libjpeg8 libgtk2-imageview-perl
  libjpeg-progs libmagick++3 transfig libset-intspan-perl
  libextutils-depends-perl libgtk2-ex-simple-list-perl libgtkimageview0 kfind
  tesseract-ocr-eng libgraphicsmagick++3 libgtk2-ex-podviewer-perl pdf2djvu
  libconfig-general-perl cuneiform-common gocr libpdf-api2-perl libtiff-tools
  perlmagick libextutils-pkgconfig-perl djvulibre-bin cuneiform
  libgoo-canvas-perl
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  gimp-data libbabl-0.0-0 libgegl-0.0-0 libgimp2.0
Suggested packages:
  gimp-help-en gimp-help libgimp-perl
The following NEW packages will be installed
  gimp gimp-data libbabl-0.0-0 libgegl-0.0-0 libgimp2.0
0 upgraded, 5 newly installed, 0 to remove and 0 not upgraded.
Need to get 7,480kB/7,922kB of archives.
After this operation, 24.6MB of additional disk space will be used.
Do you want to continue [Y/n]? y
------------------------------------------------------------------------------------------------------

Err [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) maverick/main libgimp2.0 amd64 2.6.10-1ubuntu3
  404  Not Found [IP: 194.169.254.10 80]
Err [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) maverick/main gimp-data all 2.6.10-1ubuntu3
  404  Not Found [IP: 194.169.254.10 80]
Err [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) maverick/main gimp amd64 2.6.10-1ubuntu3
  404  Not Found [IP: 194.169.254.10 80]
Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/pool/main/g/gimp/libgimp2.0_2.6.10-1ubuntu3_amd64.deb](http://gb.archive.ubuntu.com/ubuntu/pool/main/g/gimp/libgimp2.0_2.6.10-1ubuntu3_amd64.deb)  404  Not Found [IP: 194.169.254.10 80]
Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/pool/main/g/gimp/gimp-data_2.6.10-1ubuntu3_all.deb](http://gb.archive.ubuntu.com/ubuntu/pool/main/g/gimp/gimp-data_2.6.10-1ubuntu3_all.deb)  404  Not Found [IP: 194.169.254.10 80]
Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/pool/main/g/gimp/gimp_2.6.10-1ubuntu3_amd64.deb](http://gb.archive.ubuntu.com/ubuntu/pool/main/g/gimp/gimp_2.6.10-1ubuntu3_amd64.deb)  404  Not Found [IP: 194.169.254.10 80]
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?
boss@Boss-desktop:~$ 


I am at a loss, but good to know that [sudo] = root, I think

Dave

---

### Post by steeldriver on 2013-02-21
> **DaveMcC said:**
> 
I am at a loss
Dave

Possibly because 10.10 has reached its end of life --> [https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases)

If you absolutely can't upgrade, you may need to modify your software sources to use the old-releases repository --> [http://old-releases.ubuntu.com/releases/](http://old-releases.ubuntu.com/releases/)

---

### Post by DaveMcC on 2013-02-21
Upgrade to what
Ubuntu 11 - 12, no thanks, it just looks a reject of windows 8, some thing a child put together "that child was called Bill Gates"

Having looked at  the old-releases repository --> [http://old-releases.ubuntu.com/releases/](http://old-releases.ubuntu.com/releases/), I still have the CD, could I reinstall from that ?

And all because I bought a new camera

Dave

---

### Post by snowpine on 2013-02-21
Your choice; you can stick with unsupported software with potential security holes, or you can use the latest & greatest Canonical provides for free. Either way, insulting Ubuntu is not the best way to get help around here.

Here's how to get the old interface back in 12.04 (the long term support release, supported through April 2017): [http://www.psychocats.net/ubuntu/classicgnome](http://www.psychocats.net/ubuntu/classicgnome)

Then you can simply install gimp with a couple of clicks in the Software Center. :)

---

### Post by sudodus on 2013-02-21
> **DaveMcC said:**
> Upgrade to what
Ubuntu 11 - 12, no thanks, it just looks a reject of windows 8, some thing a child put together "that child was called Bill Gates"

Having looked at  the old-releases repository --> [http://old-releases.ubuntu.com/releases/](http://old-releases.ubuntu.com/releases/), I still have the CD, could I reinstall from that ?

And all because I bought a new camera

Dave
If you don't like the default desktop environment, there are several other flavours to test. Depending on the hardware you can select a suitable balance between eye-candy and speed.

- Lubuntu with the ultra light-weight desktop environment LXDE

- Xubuntu with the light-weight desktop environment XFCE (can be made to look similar to old gnome 2).

- Gnome classic with gnome 3 with or without 'desktop effects' (this is gnome with a new engine under the hood)

- Vanilla Ubuntu with the fancy desktop environment Unity

- Kubuntu with the fancy desktop environment KDE

***Edit***: Please consider upgrading to a supported version, I would suggest 12.04 LTS with long time support. At least download one or more iso files and test it live :-)

---

