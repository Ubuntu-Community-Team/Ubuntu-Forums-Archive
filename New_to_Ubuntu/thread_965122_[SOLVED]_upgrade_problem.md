---
title: "[SOLVED] upgrade problem"
date: 2008-10-31
forum: New to Ubuntu
---

### Post by karlmp on 2008-10-31
I'm upgrading from hardy to intrepid 

it stays in: fetching file 1410 of 1412

then the message pops up:

> Could not download the upgrades

The upgrade aborts now. Please check your Internet connection or installation media and try again. All files downloaded so far are kept.

Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/t/ttf-dejavu/ttf-dejavu-extra_2.25-1_all.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/t/ttf-dejavu/ttf-dejavu-extra_2.25-1_all.deb) 
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/multiverse/s/sun-java6/sun-java6-jre_6-10-0ubuntu2_all.deb](http://us.archive.ubuntu.com/ubuntu/pool/multiverse/s/sun-java6/sun-java6-jre_6-10-0ubuntu2_all.deb) 
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/t/ttf-unfonts/ttf-unfonts-core_1.0.1-7ubuntu1_all.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/t/ttf-unfonts/ttf-unfonts-core_1.0.1-7ubuntu1_all.deb)

---

### Post by fuzzygenius on 2008-10-31
This is probably just a consequence of the overloaded servers right now.  I'd wait and try again in a little bit.  Also, going to

System > Admin > Software Sources > Download from: > Other > select best server

will choose a faster mirror for you.  That may help out - hopefully you'll get put on a less-loaded server and can actually complete the download.

---

### Post by karlmp on 2008-10-31
thanks for the reply

yes, i tried that several times before asking but stays the same:(

---

### Post by ellgor on 2008-10-31
Hi,

When the error message pops up and has been closed, click straight on the upgrade icon (or restart update-manager) it should continue from where it left off and finish, mine took about ten attempts.

Regards, Ellgor.

---

### Post by karlmp on 2008-10-31
it has 3 hours downloading 

it's still in the same number (1410 of 1412) but is working

the orange line fills a little then erases back and fills again but never gets to the half of the white line. is that normal?

it seems to me that is downloading and erasing then downloading and erasing again:confused:

still in the same number (fetching file 1410 of 1412)

---

### Post by karlmp on 2008-10-31
i did a fresh install:)

**thank you all**

---

