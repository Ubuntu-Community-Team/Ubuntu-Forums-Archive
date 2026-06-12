---
title: "How to read Camera raw files in the gimp"
date: 2005-04-21
forum: Outdated Tutorials &amp; Tips
---

### Post by graigsmith on 2005-04-21
first of all check out dcraw on the web and see if your camera raw files are supported.

to install it, open synaptics package manager.

search for dcraw and install that package.
search for gimp-ufraw and install that package.

you should now be able to open the raw files, and be able to adjust a TON of import settings.

---

### Post by steil on 2005-04-22
Since it isn't listed in the howto above, the url for the DCraw website/compatability list. [http://www.cybercom.net/~dcoffin/dcraw/](http://www.cybercom.net/~dcoffin/dcraw/)

Regards, 

Steil

---

### Post by Bob D. on 2005-04-23
Yes, but until the GIMP is able to handle 16 bit images and is color management enabled, most serious digital photographers will stay in the XP world.

Bob

---

### Post by diebels on 2005-04-23
[QUOTE=Bob D.]Yes, but until the GIMP is able to handle 16 bit images and is color management enabled, most serious digital photographers will stay in the XP world.[/QUOTE]Photoshop runs fine in wine.

But I'm not that serious so I use "gimp-ufraw".
```
anders@laptop:~ $ apt-cache show gimp-ufraw
Package: gimp-ufraw
Priority: optional
Section: universe/graphics
Installed-Size: 324
Maintainer: Matthias Urlichs <smurf@debian.org>
Architecture: i386
Source: ufraw
Version: 0.4-1
Depends: libatk1.0-0 (>= 1.9.0), libc6 (>= 2.3.2.ds1-4), libgimp2.0 (>= 2.2.0+rel), libglib2.0-0 (>= 2.6.0), libgtk2.0-0 (>= 2.6.0), libjpeg62, liblcms1 (>= 1.08-1), libpango1.0-0 (>= 1.8.1), libtiff4, zlib1g (>= 1:1.2.1), gimp (>= 2.2), gimp (<< 2.3)
Conflicts: gimp-dcraw
Filename: pool/universe/u/ufraw/gimp-ufraw_0.4-1_i386.deb
Size: 91722
MD5sum: 1732a68bdc63824610a07954e8984ee8
Description: Gimp importer for raw images
 This is a graphical tool to import raw data from high-end digital cameras
 into the Gimp.
 .
 gimp-ufraw has lots of preprocessing options which seem to duplicate gimp's
 features. Unfortunately, they are necessary because its 8-bit limitation
 would cause major quality problems.
Bugs: mailto:ubuntu-users@lists.ubuntu.com
Origin: Ubuntu

```It's really nice with real time adjustment and preview of a bunch of stuff before you import it to gimp. So you don't lose as much quality as if you first imported it to gimp and then made the adjustments.

---

### Post by graigsmith on 2005-04-23
I have a digital slr. recently deleted windows.  I have found that the gimp works great for me.  the only thing thats missing is the Actions.  and the USM filter is sorta slow.

Yeah, its best to get the image as close to perfect before you import it.  that way you can take advantage of the usefulness of a 16bit image.  without gimp-ufraw it would have taken me hours to get a usable image out of each raw file.  probably hours per file.

---

### Post by TomBrooklyn on 2009-02-24
> **Bob D. said:**
> Yes, but until the GIMP is able to handle 16 bit images and is color management enabled, most serious digital photographers will stay in the XP world. Bob 
It's been a while since this was the case.  Is GIMP able to handle those things now?

---

### Post by vaxman- on 2009-03-17
> **Bob D. said:**
> Yes, but until the GIMP is able to handle 16 bit images and is color management enabled, most serious digital photographers will stay in the XP world.

Bob
I needed a good chuckle this morning...

Serious digital photographers will stay in the OS X world and use Aperture.

---

### Post by cb951303 on 2009-03-17
.

---

