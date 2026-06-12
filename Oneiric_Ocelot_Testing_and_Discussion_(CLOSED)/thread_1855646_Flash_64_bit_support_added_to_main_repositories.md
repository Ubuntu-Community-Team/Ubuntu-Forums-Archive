---
title: "Flash 64 bit support added to main repositories?"
date: 2011-10-06
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by SevenMachines on 2011-10-06
Just to check if 64 bit flash support is working from main now? And which ubuntu releases its been backported to? It'd be nice to finally get rid of the ppa, flash 64 and duke nukem in one year, who'd have thought :)

---

### Post by MacUntu on 2011-10-06
Not yet:

The following extra packages will be installed:
  flashplugin-downloader:i386

:P

---

### Post by SevenMachines on 2011-10-06
I have ```
$ apt-cache show adobe-flashplugin | grep Version
Version: 11.0.1.152-0natty1
$ apt-cache show adobe-flashplugin | grep Depends
Depends: wget, fontconfig, libatk1.0-0 (>= 1.12.4), libc6 (>= 2.4), libcairo2 (>= 1.2.4), libfontconfig1 (>= 2.8.0), libfreetype6 (>= 2.2.1), libgdk-pixbuf2.0-0 (>= 2.22.0), libglib2.0-0 (>= 2.12.0), libgtk2.0-0 (>= 2.14.0), libpango1.0-0 (>= 1.14.0), libx11-6, libxext6, libxt6
```Looking at my apt sources It looks like its coming from natty partner repository. If anyone knows what the situation is?

[EDIT] The binary shows 64 bit and its definitely not from my ppa anyway

---

### Post by Harry33 on 2011-10-06
This is from Oneiric repos (64-bit)
adobe-flashplugin 11.0.1.152-0oneiric1

> Package relationships
Depends on:
fontconfig
libatk1.0-0 (>= 1.12.4)
libc6 (>= 2.4)
libcairo2 (>= 1.2.4)
libfontconfig1 (>= 2.8.0)
libfreetype6 (>= 2.2.1)
libgdk-pixbuf2.0-0 (>= 2.22.0)
libglib2.0-0 (>= 2.12.0)
libgtk2.0-0 (>= 2.14.0)
libpango1.0-0 (>= 1.14.0)
libx11-6
libxext6
libxt6
wget

---

### Post by MacUntu on 2011-10-06
```
$ apt-cache policy adobe-flashplugin 
adobe-flashplugin:
  Installed: (none)
  Candidate: 11.0.1.152-0oneiric1
  Version table:
     11.0.1.152-0oneiric1 0
        500 [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) oneiric/partner amd64 Packages
```

\o/

So... where's 64-bit Wine? :P

---

### Post by SevenMachines on 2011-10-06
Yep, got the oneiric partners version now, is this backported to other releases then as it seems to be? Can I actually get rid of the rest of the ppa too?

---

### Post by ubj on 2011-10-06
> **SevenMachines said:**
> Yep, got the oneiric partners version now, is this backported to other releases then as it seems to be? Can I actually get rid of the rest of the ppa too?

Check out "[changes]("https://lists.ubuntu.com/")" mailing list archives.

---

