---
title: "upgrading/re-installing, 64 vs. 32 bit programs/os"
date: 2014-03-22
forum: New to Ubuntu
---

### Post by crackers_altitude on 2014-03-22
[ Ubuntu 12.04.4 LTS 32 bit (currently upgrading to 12.10)... ]
[ 64 bit Athlon w/ "lm" flags, 2.8gig total memory ]

right to the questions:
can 32bit 12.04.4 upgrade to a 64 bit Ubuntu - or does the 64 bit distribution need to go in "fresh"?
is there is a package(s) to add 32bit<->64 bit virtualization(?) with apt-get? perhaps getting [FONT=Ubuntu Mono]lib32[/FONT] somehow...
is virtualization the right word?

background:
I do not understand the interoperability of 64 and 32 bit programs with the same of the operating system. It appears there are virtualizations (that I could ask about in another thread ), but I wonder if I just upgrade it will just work without effort on my part. I read this:
[https://help.ubuntu.com/community/32bit_and_64bit](https://help.ubuntu.com/community/32bit_and_64bit)

this was the best I found for leads how to run 32 and 64 bit os/program interchangably:
[http://askubuntu.com/questions/297151/how-to-run-32-bit-programs-on-a-64-bit-system](http://askubuntu.com/questions/297151/how-to-run-32-bit-programs-on-a-64-bit-system)

---

### Post by lykwydchykyn on 2014-03-23
You can't "upgrade" from 32 bit to 64 bit.  It has to be a fresh install.

You can run 32bit applications on a 64bit install if you enable "multiarch" (which I believe is enabled by default).  You have to install some 32bit libraries, but this is usually taken care of by the package manager.

I don't think there is a way to run 64 bit applications on 32 bit.

---

### Post by Impavidus on 2014-03-23
To go from 32 to 64 bit you have to do a fresh install. With 2.8GB ram it doesn't matter too much whether you use 32 bit or 64 bit. 64 bit may be a bit faster, 32 bit can do a little more with the memory you've got.

12.10 is a dead end. It's almost end of life and its successor is end of life already (after 12.10 the support term for intermediate releases was shortened from 18 to 9 months). Users of 12.04 can best stay with 12.04 until they can upgrade/move on to 14.04.

---

### Post by crackers_altitude on 2014-03-23
that's what I needed, thanks!

---

