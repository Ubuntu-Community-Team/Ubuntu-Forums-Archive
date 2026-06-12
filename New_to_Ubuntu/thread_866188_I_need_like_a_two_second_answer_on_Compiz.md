---
title: "I need like a two second answer on Compiz"
date: 2008-07-21
forum: New to Ubuntu
---

### Post by SpiritCharge on 2008-07-21
Hey guys, I have Ubuntu 7.04 and I'm trying to implement Compiz and it doesn't seem to be working.

-Already went through the Drivers Manager and my graphics driver's enabled. I can do the giggly windows.
-Went into Synaptic Package Manager and checked every box, just double-checked and the Universe checkbox is checked.
-Reloaded Synaptic, searched for compizconfig-settings-manager and nothing comes up

First question, does Ubuntu v 7.04 not have the right files to implement compiz? I'ma noob, so I wouldn't know :)

Second, can someone walk me through this step by step?

Thanks guys!

---

### Post by YaroMan86 on 2008-07-21
Lets make it easy. Open a terminal and type:

```

ccsm

```
Because its not installed, the terminal will tell you exactly how to install the settings manager. :)

But then again... 7.04 is before Compiz-Fusion is installed by default, so you might not be using Compiz at all, really. Might wanna upgrade or install compiz from source via git.

---

### Post by Potatoj316 on 2008-07-21
I dont think you can install compiz in 7.04 but nevertheless in the terminal try ```
sudo aptitude install compizconfig-settings-manager
```

---

### Post by eragon100 on 2008-07-21
Since you say you are a noob and you have joined this forum, in july _2008_, are you sure you have 7.04 and not _8_.04? Is your version called "Hardy Heron" or "Feisty Fawn" (and does it have a heron as a background?)

---

### Post by motang on 2008-07-21
Would there be a reason why you don't want to run 8.04 on your computer?  It is after all long term support, has compiz-fusion on it and ccsm will work after you intall it from Add and Remove or from Synaptic.  Please let us know if you can't run 8.04 for some reason and if you get any error message after doing what YaroMan86 & Potatoj316 suggested.

---

### Post by billgoldberg on 2008-07-21
> **motang said:**
> Would there be a reason why you don't want to run 8.04 on your computer?  It is after all long term support, has the latest compiz-fusion on it and ccsm will work after you intall it from Add and Remove or from Synaptic.  Please let us know if you can't run 8.04 for some reason and if you get any error message after doing what YaroMan86 & Potatoj316 suggested.

Ubuntu 8.04 doesn't have the lastest compiz-fusion version on it.

It has 0.7.4, the latest is 0.7.6.

---

### Post by SpiritCharge on 2008-07-21
Alright, tried entering "ccsm" into the terminal and it came out with ```
bash: ccsm: command not found
```

And I entered the sudo code, and it came up with this

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Initializing package states... Done
Building tag database... Done      
Couldn't find any package whose name or description matched "compizconfig-settings-manager"
The following packages have been automatically kept back:
  kdelibs-data kdelibs4c2a libpcre3 
  linux-image-generic linux-libc-dev 
  linux-restricted-modules-common 
  linux-restricted-modules-generic 
The following packages have been kept back:
  bind9-host bzip2 ca-certificates cupsys 
  cupsys-common dnsutils evolution 
  evolution-common evolution-plugins firefox 
  firefox-gnome-support gnome-btdownload gnupg 
  gpgv gs-esp gs-esp-x gstreamer0.10-esd 
  gstreamer0.10-plugins-good gthumb hal 
  hal-device-manager language-pack-en 
  language-pack-gnome-en lftp libbind9-0 
  libbz2-1.0 libcdio6 libcupsimage2 libdns22 
  libgs-esp8 libhal-storage1 libhal1 
  libhsqldb-java libicu36 libisc11 libisccc0 
  libisccfg1 libkrb53 liblwres9 libnspr4 libnss3 
  libpoppler1 libpoppler1-glib libsmbclient 
  libspeex1 linux-generic linux-headers-2.6.20-16 
  linux-headers-2.6.20-16-generic 
  linux-headers-generic 
  linux-image-2.6.20-16-generic nvidia-glx 
  openoffice.org openoffice.org-base 
  openoffice.org-calc openoffice.org-common 
  openoffice.org-core openoffice.org-draw 
  openoffice.org-filter-mobiledev 
  openoffice.org-gnome openoffice.org-gtk 
  openoffice.org-impress 
  openoffice.org-java-common openoffice.org-math 
  openoffice.org-style-human openoffice.org-writer 
  openssh-client poppler-utils python-uno 
  rhythmbox rsync samba-common smbclient 
  ssh-askpass-gnome ssl-cert ttf-opensymbol tzdata 
  unzip update-manager update-manager-core 
  xserver-xorg-core 
0 packages upgraded, 0 newly installed, 0 to remove and 87 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.

```

Haha, so I guess the better question right now is: How do I update Ubuntu to the latest version :)

---

### Post by SpiritCharge on 2008-07-21
Yeah, its Feisty Fawn, 7.04 :P

---

### Post by Ryadt on 2008-07-21
> **SpiritCharge said:**
> Yeah, its Feisty Fawn, 7.04 :P

If you got working internet, you can update via the update manager. But I personally would download the latest version and do a complete installation.

---

### Post by SpiritCharge on 2008-07-21
Ok, going through and updating system to newest version, i'll get back to you guys in a few

---

### Post by RomeReactor on 2008-07-21
> **SpiritCharge said:**
> Haha, so I guess the better question right now is: How do I update Ubuntu to the latest version :)

Hi. Had you been running Dapper (Ubuntu 6.06) you could have updated directly to 8.04; as it is, though, you would need to go from 7.04->7.10->8.04. If you don't mind re-installing, this would be the fastest way.

If you want to keep Feisty, you can get Compiz and the settings manager like this:
```
sudo aptitude install compiz gnome-compiz-manager
```

EDIT: Posted a little late and didn't see you're already upgrading.

---

### Post by sailor2001 on 2008-07-21
You could stay were you are and synaptic BERYL which will give you almost everything you're looking for. Compiz merged with beryl and became compiz-fusion for later ubuntu series.

---

