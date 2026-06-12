---
title: "where to get GIMP 2.5.1 for ubuntu 8.04?"
date: 2008-06-23
forum: New to Ubuntu
---

### Post by legolas_w on 2008-06-23
Ubuntu come with an old version of gimp, is there any deb package for gimp 2.5.1 for ubuntu 8.4?

Thanks

---

### Post by Rhubarb on 2008-06-23
I doubt if someone would create a deb package for GIMP 2.5.x, as 2.5 is purely a development release working up to a 2.6.x stable release.

You should still be able to compile GIMP 2.5.1 yourself, and there's a chance it'll be stable enough to work on, and there's a chance someone may offer a deb package of GIMP 2.5.1 somewhere.
Personally I'm looking forward to trying out GIMP 2.5.x / 2.6.x because of the new GEGL backend supports higher colour bit depths and better CMYK support :)

---

### Post by _sphinx_ on 2008-06-23
Refer to this for deb:
[http://ubuntuforums.org/showthread.php?t=791055](http://ubuntuforums.org/showthread.php?t=791055)
What's wrong in compiling through tar.gz at:
[ftp://ftp.gimp.org/pub/gimp/v2.5/](ftp://ftp.gimp.org/pub/gimp/v2.5/)

---

### Post by ad_267 on 2008-06-23
Ubuntu comes with the latest stable release of GIMP. 2.5 is a development release so you will have to compile it yourself.

---

### Post by bumanie on 2008-06-23
Gimp 2.5.1 is only available as a .tar.bz2, it is a development version on the way to stable version 2.6.

---

### Post by T-Virus on 2008-06-23
Hmmm what's wrong with the version you can get of repos? It's the latest stable version and it doesn't require much effort installing.

---

### Post by olskar on 2008-06-24
> **legolas_w said:**
> Ubuntu come with an old version of gimp, is there any deb package for gimp 2.5.1 for ubuntu 8.4?

Thanks


Here you go :)

[http://in.solit.us/archives/download/146113](http://in.solit.us/archives/download/146113)

Edit: I saw now that there was missing dependency..sorry about that..perhaps you can solve it :)

---

### Post by kaltv on 2008-07-05
Thank you so much for the .deb! :D

To me, it complained about not having the right version of libpango1.0-0

I ended up fetching the latest version of libpango in the Debian Sid repositories. Basically:

Get libpango1.0-common:
[http://packages.debian.org/sid/libpango1.0-common](http://packages.debian.org/sid/libpango1.0-common)

Get libpango1.0:
[http://packages.debian.org/sid/libpango1.0-0](http://packages.debian.org/sid/libpango1.0-0)

(choose the right architecture and choose a mirror. For those not familiar, you're most likely on i386 )

Now open a terminal, then dpkg -i the libpango1.0-common, then libpango1.0, then Gimp-2.5.1 deb packages.

It should work now! Much thanks to olskar for the .deb!

---

