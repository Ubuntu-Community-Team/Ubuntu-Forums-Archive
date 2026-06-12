---
title: "Lubuntu Installation Fails"
date: 2018-11-09
forum: New to Ubuntu
---

### Post by 1usmc on 2018-11-09
I am trying to install lubuntu on an older Dell Lattitude.  Spects are 1GHz Processor, 1 Gig RAM, brand new 40gig HD.

Dowloaded and burned iso file from lubuntu.me  Version 18.10 32 bit Desktop (does it matter that I am loading to a laptop?  I don't see a download for laptops.)

When I try to install, I get the following message: "Failed to load ldlinux.c32"

What do I do now?

I might also mention, if I try to then boot up I get a message: "NTLDR is missing"

I also tried downloading the iso from lubuntu.net.  I don't get the failed message, but I still get the "NTLDR is missing" message.

---

### Post by MoebusNet on 2018-11-09
Without knowing what model CPU you have (Pentium, Pentium-M, AMD, etc.) it is difficult for me to be very specific, however please allow me to offer a couple of resources that may help -

[https://help.ubuntu.com/community/Installation](https://help.ubuntu.com/community/Installation)

If you have a Pentium-M CPU, the *forcepae* boot option will be required -

[https://help.ubuntu.com/community/PAE](https://help.ubuntu.com/community/PAE)

By the way, starting with 18.10, I believe that CPU's prior to the i686 are no longer supported (check release notes). You may have better luck with 18.04 (I use Lubuntu for old machines).

If these links help you with your installation attempt, please mark this thread as 'SOLVED' in 'Thread Tools'.

---

### Post by Autodave on 2018-11-09
That error is a Windows error??  I have never heard of it on Linux, but I sure don't know everything.  Are you trying to dual boot this machine?  What version of Windows is/was it running?  And as already asked for, some specs on your machine could be very helpful.

---

