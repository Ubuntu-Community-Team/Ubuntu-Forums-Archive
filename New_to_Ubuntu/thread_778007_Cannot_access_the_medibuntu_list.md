---
title: "Cannot access the medibuntu list"
date: 2008-05-01
forum: New to Ubuntu
---

### Post by phread59 on 2008-05-01
I just did a fresh install of 8.04 after a botched update through update manager.  So I'm starting out fresh again and have to reconfigure everything.  So I'm trying to get encrypted dvd's to play again.  I try to acess the medibuntu list for Hardy and I get an "error 404 not found".  I cannot acess it to get libdvdcss2 and the w32codecs.  Any suggestions?  How about some way to get them from outside Ubuntu and install.  I did install the restricted extras.  But css2 and the codecs were not in the extras file.

Mark Shuman

---

### Post by mc4man on 2008-05-01
ck. here to double check medibuntu or link to libdvdcss2
[http://ubuntuforums.org/showthread.php?p=4837872#post4837872](http://ubuntuforums.org/showthread.php?p=4837872#post4837872)

w32codecs - [http://packages.medibuntu.org/pool/non-free/w/](http://packages.medibuntu.org/pool/non-free/w/)

---

### Post by phread59 on 2008-05-01
MC4, I totally get that.  I have tried at least 6 different versions of that command.  I keep getting "error 404 not found".  It is like the medibuntu file is just not there!  I am not sure how to proceed without it.  I have been trying to find a simple tutorial to download and install just css2 and the w32 codecs but I keep running headlong into some form of Sudo wget.  It just won't work.  There either is a problem with the medibuntu file or it was moved.  Wish it was simple and straight forward.

Mark Shuman

---

### Post by phread59 on 2008-05-01
OK got this one nailed down.  I just added the Debian multimedia sources to my list and updated them in and installed.  I verified they are there with Synaptic.  Should be good to go.

Mark Shuman

---

