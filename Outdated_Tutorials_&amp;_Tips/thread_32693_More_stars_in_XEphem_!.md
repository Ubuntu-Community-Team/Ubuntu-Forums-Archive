---
title: "More stars in XEphem !"
date: 2005-05-09
forum: Outdated Tutorials &amp; Tips
---

### Post by thierry on 2005-05-09
Ok this is not a frequently asked question but I found the following very useful. XEphem is probably the best astronomical software available for Ubuntu. You can download the debian package from here :
 
[http://ftp.debian.skynet.be/ftp/debian/pool/non-free/x/xephem/]("http://ftp.debian.skynet.be/ftp/debian/pool/non-free/x/xephem/")
 
Now the problem is that this is a commercial program. The free download has a limited catalogue of stars compared to the version you buy. You can go around that by downloading the very precise Hipparcos catalogue of stars from here :
 
[http://www.yvonnet.org/xephem/]("http://www.yvonnet.org/xephem/")
 
Copy the file hipparcos.edb to your /usr/share/xephem/catalogs folder (this is where I found it, but it seems to install sometimes in /usr/X11R6/Xephem/catalogs and /usr/X11R6/share/xephem/catalogs. I downloaded from another link, so this is if you had XEphem already). Then open XEphem and go to Data, Files, Files to load the hipparcos catalogue. This will give you 118209 more stars in your sky.
 
Enjoy !

---

### Post by Gandalf on 2005-05-09
[QUOTE=thierry]Ok this is not a frequently asked question but I found the following very useful. XEphem is probably the best astronomical software available for Ubuntu. You can download the debian package from here :

[http://ftp.debian.skynet.be/ftp/debian/pool/non-free/x/xephem/]("http://ftp.debian.skynet.be/ftp/debian/pool/non-free/x/xephem/")

Now the problem is that this is a commercial program. The free download has a limited catalogue of stars compared to the version you buy. You can go around that by downloading the very precise Hipparcos catalogue of stars from here :

[http://www.yvonnet.org/stuff/xephem/]("http://www.yvonnet.org/stuff/xephem/")

Copy the file hipparcos.edb to your /usr/share/xephem/catalogs folder (as root of course). Then open XEphem and go to Data, Files, Files to load the hipparcos catalogue. This will give you 118209 more stars in your sky.

Enjoy ![/QUOTE]
 can't get it to work
xephem: error while loading shared libraries: libXm.so.1: cannot open shared object file: No such file or directory

---

### Post by thierry on 2005-05-09
Sorry about that. On my laptop install was very smooth. I was actually surprised.

Now I don't know if this can help but in my /usr/lib/ folder I have a libXm.so.2 file...

---

### Post by Gandalf on 2005-05-09
actually it worked alone :o
i tried it now it worked, i only installed rox-filer since! :o
anyway update your tuto it's /usr/X11R6/share/xephem/catalogs

---

### Post by LoneStarM3 on 2005-09-21
[QUOTE=thierry]Ok this is not a frequently asked question but I found the following very useful. XEphem is probably the best astronomical software available for Ubuntu. You can download the debian package from here :

[http://ftp.debian.skynet.be/ftp/debian/pool/non-free/x/xephem/]("http://ftp.debian.skynet.be/ftp/debian/pool/non-free/x/xephem/")

Now the problem is that this is a commercial program. The free download has a limited catalogue of stars compared to the version you buy. You can go around that by downloading the very precise Hipparcos catalogue of stars from here :

[http://www.yvonnet.org/stuff/xephem/]("http://www.yvonnet.org/stuff/xephem/")

Copy the file hipparcos.edb to your /usr/share/xephem/catalogs folder (this is where I found it, but it seems to install sometimes in /usr/X11R6/Xephem/catalogs and /usr/X11R6/share/xephem/catalogs. I downloaded from another link, so this is if you had XEphem already). Then open XEphem and go to Data, Files, Files to load the hipparcos catalogue. This will give you 118209 more stars in your sky.

Enjoy ![/QUOTE]
 The download given, [http://ftp.debian.skynet.be/ftp/debian/pool/non-free/x/xephem/](http://ftp.debian.skynet.be/ftp/debian/pool/non-free/x/xephem/) is for ver3.4-5, which is good.  But the best is ver3.7.  Although it is sold as commerical CD package version, the author provides source code and a link to the required motif files @ [http://www.clearskyinstitute.com/xephem/](http://www.clearskyinstitute.com/xephem/) [so you can compile your own copy for non-commercial use]

I have 3.7 [from the source code] running on ubuntu 5.04.  There is a change from earlier versions in how the sites files are handled, and you have to specify your browser [i.e., firefox, opera, etc, and browser must be loaded if you want help files displayed]  but you can download the complete 3.7 user manual from the xephem website.

At this point I don't know how to make a .deb package for it, but if there is some interest maybe I can get my son [my serious linux guru] to figure it out.

---

### Post by thierry on 2005-09-23
This howto was quite old already, thanks a lot for the update :)

---

