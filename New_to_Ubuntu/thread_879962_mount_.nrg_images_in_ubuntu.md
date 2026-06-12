---
title: "mount .nrg images in ubuntu"
date: 2008-08-04
forum: New to Ubuntu
---

### Post by melrokz on 2008-08-04
Hi! I'm Melvin from India.
I'd like 2 mount .nrg and .iso files in ubuntu. i already have nero linux, but there is no feature 2 mount the image files. Please tell me what software can do this for me.

---

### Post by bobnutfield on 2008-08-04
I believe the Nero files must be converted to .iso first.  I have not done it, but here is a site with some forum posts on the subject:

[http://forums.whirlpool.net.au/forum-replies-archive.cfm/499696.html]("http://forums.whirlpool.net.au/forum-replies-archive.cfm/499696.html")

---

### Post by Troll_the_Great on 2008-08-04
Try AcetoneIso2.It's free and ca mount .iso and .nrg.
Open a terminal and type:
```
sudo apt-get install acetoneiso2
```
Cheers!

---

### Post by cariboo on 2008-08-04
You could also try nrg2iso, it is available in the repositories

Jim

---

### Post by DarkSim on 2008-08-08
There is a package called gisomount in the repositories. Works great for me.

---

### Post by kpkeerthi on 2008-08-08
+1 for acetoneiso

> **AcetoneISO Features**

    * Mount and Unmount ISO, MDF, NRG (if iso-9660 standard)
    * Convert / Extract / Browse to ISO : *.bin *.mdf *.nrg *.img *.daa *.cdi *.xbx *.b5i *.bwi *.pdi
    * Play a DVD Movie ISO with most used media players
    * Generate an ISO from a Folder or CD/DVD
    * Generate MD5 file of an image
    * Encrypt an image
    * Split image in X megabyte
    * Compress with High Ratio an image
    * Rip a PSX cd to *.bin to make it work with epsxe/psx emulators
    * Service-Menu support for Konqueror
    * Restore a lost CUE file of *.bin *.img


[How to]("http://www.ubuntugeek.com/mount-and-unmount-isomdfnrg-images-using-acetoneiso-gui-tool.html")

---

### Post by kajillin on 2008-08-08
yes acetoneiso is a very good program. Ive noticed alot of douchebags have been putting malicious code in .nrg format, be careful where u got the image from.

---

### Post by hyper_ch on 2008-08-08
.nrg files can be mounted like .iso files very simply from the cli.

---

### Post by Existance0 on 2008-08-11
```
sudo apt-get install nrg2iso
```
then cd to the folder where your nrg file is
```
nrg2iso [filename].nrg [filename].iso
```

---

