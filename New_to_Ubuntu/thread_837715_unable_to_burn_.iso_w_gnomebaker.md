---
title: "unable to burn .iso w/ gnomebaker"
date: 2008-06-22
forum: New to Ubuntu
---

### Post by fiskking on 2008-06-22
I was successful in making an .iso file using DeVeDe. Upon trying to burn .iso file to Dvd using GnomeBaker I received the following error upon completion:



```
Executing 'builtin_dd if=/home/fisk/death_proof.iso of=/dev/sr1 obs=32k seek=0'
/dev/sr1: "Current Write Speed" is 2.5x1352KBps.
/dev/sr1: flushing cache
:-[ SYNCHRONOUS FLUSH CACHE failed with SK=3h/ASC=A0h/ACQ=80h]: Input/output error
```

can anyone help?

---

### Post by Biggy on 2008-06-22
try to burn with Brasero

---

### Post by fiskking on 2008-06-22
does the ¨synchronous flush cache¨ have anything to do w/ my memory? i have roughly 7gig left on hard drive

---

### Post by subaruwrc01 on 2008-06-22
Sorry I can't answer your question.

I recommend using K3B for burning.  It's an all-in-one burning tool that is very useful.

---

### Post by RomeReactor on 2008-06-22
Hi. Try using Nautilus to burn the ISO: With a blank DVD in the drive, right-click on the ISO and select 'Write to Disc'.

EDIT: If you have a Pioneer DVD burner or an older motherboard the problem might be related to [this bug]("https://bugs.launchpad.net/ubuntu/+source/dvd+rw-tools/+bug/70485").

---

