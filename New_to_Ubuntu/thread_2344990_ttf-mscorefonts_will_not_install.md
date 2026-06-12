---
title: "ttf-mscorefonts will not install"
date: 2016-11-29
forum: New to Ubuntu
---

### Post by jim Kane on 2016-11-29
Xubuntu 16.04 
I have googled this extensively but cont find an answer
Ttf-mscorefonts will not fully install error message below
Thanks for any help

W: Can't drop privileges for downloading as file '/var/lib/update-notifier/package-data-downloads/partial/courie32.exe' couldn't be accessed by user '_apt'. - pkgAcquire::Run (13: Permission denied)
ttf-mscorefonts-installer: downloading [http://downloads.sourceforge.net/corefonts/georgi32.exe](http://downloads.sourceforge.net/corefonts/georgi32.exe)
Err:1 [http://downloads.sourceforge.net/corefonts/georgi32.exe](http://downloads.sourceforge.net/corefonts/georgi32.exe)
  404  Not Found
W: Can't drop privileges for downloading as file '/var/lib/update-notifier/package-data-downloads/partial/georgi32.exe' couldn't be accessed by user '_apt'. - pkgAcquire::Run (13: Permission denied)
E: Failed to fetch [https://netix.dl.sourceforge.net/project/corefonts/the](https://netix.dl.sourceforge.net/project/corefonts/the) fonts/final/georgi32.exe  404  Not Found

---

### Post by slickymaster on 2016-11-29
That's a known bug. See [https://bugs.launchpad.net/debian/+source/synaptic/+bug/1522675](https://bugs.launchpad.net/debian/+source/synaptic/+bug/1522675)

A workaround is to download the 3.6 version of ttf-mscorefonts-installer from debian [https://packages.debian.org/en/sid/all/ttf-mscorefonts-installer/download](https://packages.debian.org/en/sid/all/ttf-mscorefonts-installer/download) and installing that package with Software Center or by using the terminal.

---

### Post by jim Kane on 2016-11-29
Thanks for your help, may need to come back and ask how to install package but have marked solved

---

### Post by howefield on 2016-11-30
> **jim Kane said:**
> ... and ask how to install package but have marked solved

```
wget http://ftp.de.debian.org/debian/pool/contrib/m/msttcorefonts/ttf-mscorefonts-installer_3.6_all.deb -P ~/Downloads
```

will download the package to your Downloads folder, and
 
```
sudo apt install ~/Downloads/ttf-mscorefonts-installer_3.6_all.deb
```

will install the package.

---

### Post by Crimple on 2016-12-01
Was having the same issue and this solved it, thanks.

---

### Post by jim Kane on 2016-12-01
> **howefield said:**
> ```
wget http://ftp.de.debian.org/debian/pool/contrib/m/msttcorefonts/ttf-mscorefonts-installer_3.6_all.deb -P ~/Downloads
```

will download the package to your Downloads folder, and
 
```
sudo apt install ~/Downloads/ttf-mscorefonts-installer_3.6_all.deb
```

will install the package.

yes thanks googleing worked for me this time, :) so installed and working the same night

Jk

---

### Post by heldal2 on 2016-12-07
The updated installer in version 3.6 attempts to work around the problem by addressing specific sourceforge-mirrors for download. It is just a band-aid and may not work from all locations. The problem here is that the HTTP-client used by the installer to download the fonts is struggling with Sourceforge's use of javascripts to pedal ads and redirect downloads. The proper solution would be to host the fonts on a less complex server elsewhere, or to use a more capable HTTP-client for download in the install-script.

---

