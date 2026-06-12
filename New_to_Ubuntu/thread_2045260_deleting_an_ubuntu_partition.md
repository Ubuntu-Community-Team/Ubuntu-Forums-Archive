---
title: "deleting an ubuntu partition"
date: 2012-08-20
forum: New to Ubuntu
---

### Post by djyoung4 on 2012-08-20
So I have a server that is currently running 10.04.  The Harddrive breakdown is a 2 TB harddrive with my filesystem installed on it there and then two 1 TB harddrives used as just storage.  I want to install 12.04 on another 40 GB harddrive that I recently got and get rid of the 10.04 install on the 2 TB harddrive and make it just more storage.  Would it be better to first delete the 10.04 install or install 12.04 on the 40 GB harddrive?  Any help is greatly appreciated.

---

### Post by Bashing-om on 2012-08-20
dj-:
 hi, I may not be the sharpest tack in this box ....but, this is what I would do.

 first install 12,04 on the 40 megger ... make sure all is kosher ,, and I liked all i looked at.
  then ...... I would format the 10.04 drive and reset up additional partitions.
  update grub so it reflects the changes.
    Lastly I would edit the fstab in accordance with my needs.

[INDENT]kindest regards <==BDQ
[/INDENT]

---

### Post by djyoung4 on 2012-08-20
thats what I was thinking but just didn't want to have to deal with booting multiple OS's

---

### Post by Bashing-om on 2012-08-20
dj---
 No big deal to choose what ya want to boot ... I would 'till I had 12.04  down pat ... and set all-the-way-up as I wanted....then do away with 10.04 (solid as a rock finally on my computer---after all this I do not look forward to learning 12.04 !)

[INDENT] hth <==BDQ
[/INDENT]

---

### Post by NoTryDO on 2012-08-21
why not install startupmanager

Grub, Usplash and Splash screen configuration

and tell it use 12:04 as default - test run for few days - then delete 10 an then change fstab

---

