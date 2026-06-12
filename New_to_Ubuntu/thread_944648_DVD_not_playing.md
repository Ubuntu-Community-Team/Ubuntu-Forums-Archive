---
title: "DVD not playing"
date: 2008-10-11
forum: New to Ubuntu
---

### Post by loyaleagle on 2008-10-11
I tried to play DVDs for the first last night and kept getting an error. Ubuntu recognizes the CD drive and regular data CDs work great.

Do you need to install additional codecs or are they all included with Ubuntu. I tried to play the dvd with VLC Media Player, Movie Player and Mplayer. None worked.... 

I am at a loss as to troubleshoot this problem, but know that it is probably an easy fix (like everything in Ubuntu)

Thanks.

---

### Post by SunnyRabbiera on 2008-10-11
yeh to play DVD's you need extra packages, like libdvdcss.
There is a repository with all you will need to get multimedia working:
[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

medibuntu is a third party repository that has done many a great service.

---

### Post by Orange_and_Green on 2008-10-11
Hello :)

Have you tried installing libdvdcss2 from Medibuntu as decribed here? (howto and legal stuff)

[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

If that fails, you might also try installing the various gstreamer codecs from Synaptic. Or trying a few other players like Xine or Ogle. 

Good luck :KS

---

### Post by loyaleagle on 2008-10-11
Yes, I have Medibuntu already in my repositories, but do not know what to install from it?

Thanks.

---

### Post by minky311 on 2008-10-11
[http://packages.medibuntu.org/hardy/libdvdcss2.html](http://packages.medibuntu.org/hardy/libdvdcss2.html)
You can download just this one package from here if you don't want to add the repositories or just follow the guide that was already posted.

---

### Post by SunnyRabbiera on 2008-10-11
> **loyaleagle said:**
> Yes, I have Medibuntu already in my repositories, but do not know what to install from it?

Thanks.

the packages you will need to install are libdvdcss, libdvdread and libdvdnav.
That should be all that you need.

---

### Post by Keen101 on 2008-10-11
Yeah, to play encrypted DVD's you need to install additional codecs. mainly the libdvdcss2...

try reading this:

[http://geekybits.blogspot.com/2007/10/playing-encrypted-dvds-in-ubuntu-710.html](http://geekybits.blogspot.com/2007/10/playing-encrypted-dvds-in-ubuntu-710.html)

---

