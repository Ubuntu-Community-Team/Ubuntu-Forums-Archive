---
title: "Save all OS configurations?"
date: 2008-11-22
forum: New to Ubuntu
---

### Post by Sunshine1987 on 2008-11-22
My friend particularly likes my Ubuntu 8.10 configuations, everything from my default theme and programs all the way to my Firefox tweaks.  Is there any way that I can create a LiveCD of my OS that will automatically configure these upon installation?  I tried Remastersys Backup, but it tells that it'll take up too much space.  I already created a Remastery Dist LiveCD, but it doesn't have all my settings/tweaks immediately following installation.  I would also really like to have a backup LiveCD in case my system crashes somehow.

Am I not using the Remastersys Backup mode properly, or is there a better way to do this?

Thanks a lot!

---

### Post by jpkotta on 2008-11-22
> **Sunshine1987 said:**
> My friend particularly likes my Ubuntu 8.10 configuations, everything from my default theme and programs all the way to my Firefox tweaks.  Is there any way that I can create a LiveCD of my OS that will automatically configure these upon installation?  I tried Remastersys Backup, but it tells that it'll take up too much space.  I already created a Remastery Dist LiveCD, but it doesn't have all my settings/tweaks immediately following installation.  I would also really like to have a backup LiveCD in case my system crashes somehow.

Am I not using the Remastersys Backup mode properly, or is there a better way to do this?

Thanks a lot!

It will probably be enough to copy your $HOME, rather than the whole system.
```
cd /tmp
tar zcf home-$(date +%F).tar.gz . -C $HOME --exclude big_directory_that_I_dont_want_backed_up
```

---

### Post by Keen101 on 2008-11-22
maybe also copying /usr/lib/firefox in addition to $home. But i don't really know since i've never tried.

---

### Post by jpkotta on 2008-11-22
> **Keen101 said:**
> maybe also copying /usr/lib/firefox in addition to $home. But i don't really know since i've never tried.

Probably not.  Anything in there should have been installed by a package.  You can't change it without being root.

---

### Post by Sunshine1987 on 2008-11-23
Thank you for the quick replies!  I will take your suggestion, jpkotta, but how would I integrate that into a fresh installation of Ubuntu on a different computer?  Also, I'm particularly interested in using Remastersys, if at all possible, to create an actual LiveCD of my distro.  Any advice?

---

### Post by jpkotta on 2008-11-23
On the new machine:
```
cd 
tar xf home-2008-11-13.tar.gz
```

This will overwrite files that are already in the directory and in the archive.  Extract it somewhere else and copy with discretion if this concerns you.

I've never used Remastersys.

---

