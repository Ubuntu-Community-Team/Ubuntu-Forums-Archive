---
title: "How to patch with a diff file?"
date: 2011-06-27
forum: Packaging and Compiling Programs
---

### Post by frogotronic on 2011-06-27
Hi,

  On Natty, the mail-notification-evolution package installs but fails to load.  See Debian Bug here: [http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=617771](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=617771)

  I'd like to try and patch the Ubuntu build of the deb package with the posted diff/patch file.  I've read several articles on this, but as I've never done this - it's confusing.

  How do I apply a diff file to a deb?  (See attached archive for the two files)

Thanks,
CH      :(

---

### Post by scott-ian on 2011-06-27
I haven't done it, but you use a program called patch.  Type "man patch" for the manual on use of the program.

---

### Post by MadCow108 on 2011-06-27
[https://wiki.ubuntu.com/PackagingGuide/Recipes/Debdiff?action=show&redirect=MOTU%2FRecipes%2FDebdiff#Applying_a_Debdiff](https://wiki.ubuntu.com/PackagingGuide/Recipes/Debdiff?action=show&redirect=MOTU%2FRecipes%2FDebdiff#Applying_a_Debdiff)
but the patch in the debian bug might not apply on the ubuntu package.

---

### Post by Yellow Pasque on 2011-06-30
The patch does apply cleanly. The package uses quilt for patching. 
[https://wiki.ubuntu.com/PackagingGuide/Complete#quilt_.28Example_Package:_xterm.29](https://wiki.ubuntu.com/PackagingGuide/Complete#quilt_.28Example_Package:_xterm.29) The correct way to do something like this is:
```
sudo apt-get build-dep mail-notification
sudo apt-get install quilt (and whatever else you need)
cd ~/; mkdir source; cd source
apt-get source mail-notification
cd mail-notification-5.4.dfsg.1/
export QUILT_PATCHES=debian/patches
quilt push -a
quilt new evolution-plugin.patch
quilt add src/nm-evolution-server.gob
patch -p1 < *<path_to_patch>*
quilt refresh
quilt pop -a
dch -i
debuild -B -us -uc
cd ..
sudo dpkg -i mail-notification_5.4.dfsg.1*.deb
```

I've built it for you in mediahacks PPA. Just get the packages you need and install them manually (rather than adding the whole PPA). [https://launchpad.net/~dtl131/+archive/mediahacks](https://launchpad.net/~dtl131/+archive/mediahacks)

---

