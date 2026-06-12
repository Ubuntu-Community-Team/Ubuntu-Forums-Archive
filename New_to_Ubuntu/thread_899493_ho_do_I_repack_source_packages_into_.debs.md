---
title: "ho do I repack source packages into .debs?"
date: 2008-08-24
forum: New to Ubuntu
---

### Post by snkiz on 2008-08-24
well I finally got fed up with gnome-screensaver not restoring graphics settings. So I downloaded the source and the patch and fixed it. (yea me!) but now I would like to install it, but I don't know how to repack it. So anyone know how to do this? 

Thanks in advance :) 

P.S I know I could use ./configure & make install but I want a proper .deb

---

### Post by porchrat on 2008-08-24
why not use dpkg worked on my ATI driver binaries

---

### Post by bobbocanfly on 2008-08-24
It would be better to send your patch to the developers, so it would then filter down to the Ubuntu developers and be released to everybody.

---

### Post by snkiz on 2008-08-24
thats where I got the patch [https://bugs.launchpad.net/gnome-screensaver/+bug/33214]("https://bugs.launchpad.net/gnome-screensaver/+bug/33214")

---

### Post by snkiz on 2008-08-24
um.. not familar with how to do that either, took long enough to figure out how to put in the patch in the first place, this is new ground for me.

---

### Post by Oldsoldier2003 on 2008-08-24
"Fix Released" means it is now in the repos and will be available through updates or in the next distibution.

However many packages have issues because of inconsistencies in usage. see [https://bugs.launchpad.net/malone/+bug/163694](https://bugs.launchpad.net/malone/+bug/163694) for what I mean there...


edit: I made this comment to explain the issue related to the patch he references. Making a Debian package is probably not worth the trouble to be honest. However if you do its best to upload it to your PPA if you plan on making the binary available. If you properly increment the package version with ~ppa it will not be a problem when the official patch is incorporated)

---

### Post by forger on 2008-08-24
I think you're looking for guides like:
[https://wiki.ubuntu.com/PackagingGuide/](https://wiki.ubuntu.com/PackagingGuide/)
[https://wiki.ubuntu.com/PackagingGuide/Basic](https://wiki.ubuntu.com/PackagingGuide/Basic)

---

### Post by snkiz on 2008-08-24
maybe its fixed in interpid but not hardy

---

### Post by Vivaldi Gloria on 2008-08-24
> **Oldsoldier2003 said:**
> "Fix Released" means it is now in the repos and will be available through updates or in the next distibution.

At last. :-)

---

### Post by unutbu on 2008-08-24
You could instead use checkinstall:
```

sudo apt-get install checkinstall
sudo checkinstall --fstrans=no -D make install
```

The above checkinstall command will make a .deb package instead of installing the files directly into your system. This way you can then install it with
```

sudo dpkg -i NAME-OF-DEB.deb
```

and also uninstall it:
```

sudo dpkg -r NAME-OF-PACKAGE
```

---

### Post by snkiz on 2008-08-24
while I apericieate the education in packaging (much needed :) ) I just wanted to repack it so its easy to reinstall if/when I reinstall my system cuz I screwed with it too much. lol I would not deam of uploading my amaturish work to inflict on others I don't have a ppa, although that may be a good idea latter. checkinstall sounds more like what I need right now thanks.

---

