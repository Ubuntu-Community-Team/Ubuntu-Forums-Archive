---
title: "[Cross Posting] Upgraded to Hardy, octave 3.0.0 does not start"
date: 2008-06-24
forum: Programming Talk
---

### Post by ayesha kalra on 2008-06-24
Hi all

I just upgraded to Hardy and found that octave is not starting now. This is the error message I am getting

```

octave: error while loading shared libraries: libumfpack.so.1: cannot open shared object file: No such file or directory

```

Obviously, I do not have libumfpack.so.1, or do not have it at the right location, or there is a name change involved. Any suggestions here will be helpful.

Thanks
Ayesha

---

### Post by LaRoza on 2008-06-24
Try this:

```
sudo apt-get update && sudo aptitude install libsuitesparse-3.1.0
```

---

### Post by ayesha kalra on 2008-06-24
I already did 

sudo apt-get update

This is what I get for the second command

Reading package lists... Done
Building dependency tree       
Reading state information... Done
libsuitesparse-3.1.0 is already the newest version.

---

### Post by ayesha kalra on 2008-06-24
I think this is the problem

libumfpack.so.1 has been replaced by libumfpack.so.3.1.0 (I see libumfpack.so.3.1.0 in my /usr/lib ). But how do I tell Octave to look for libumfpack.so.3.1.0 instead of libumfpack.so.1


Ayesha

---

### Post by LaRoza on 2008-06-24
> **ayesha kalra said:**
> I think this is the problem

libumfpack.so.1 has been replaced by libumfpack.so.3.1.0 (I see libumfpack.so.3.1.0 in my /usr/lib ). But how do I tell Octave to look for libumfpack.so.3.1.0 instead of libumfpack.so.1


Ayesha

Upgrades often do this. I recommend reinstalling Octave (uninstall previous)

---

