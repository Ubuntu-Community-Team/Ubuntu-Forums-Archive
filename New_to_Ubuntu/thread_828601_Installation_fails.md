---
title: "Installation fails"
date: 2008-06-13
forum: New to Ubuntu
---

### Post by ON5MJ on 2008-06-13
Hi, from a newbie in Ubuntu

Config:
AMD Athlon 64 X2 dual / core processor 3800+ / 2.01 GHz
3 GB ram
Nvidia GForce 7600 GS
screen 1: Samsung Syncmaster 913N 19"
screen 2: Acer AL2423W 24"

Trial 1
-------
ISO 8.04 64 bits dowloaded and engraved on a DVD

Installation starts (language -> orange bar). After a few minutes both screens become scrambled (sync), and the process stops or pends. Probably behind the scrambled screen 1 there is something to do that I can't read.


Trial 2
-------
Live CD 32 bits (from a magazine).

Same results than trial 1 excepted that I can ear the opening sound of Ubuntu. Then the process stops or pends.


Looks like a video card recognition problem for theses flat screens (that nevertheless work well together in XP pro)

Somebody has an idea ?

Thanks.

---

### Post by tamoneya on 2008-06-13
if you go into the boot options there should be a safe boot option.  This should allow for your graphics card to be properly detected.

---

### Post by canthus13 on 2008-06-13
So you're stuck while trying to install?  Try reburning the CD/DVD at the slowest speed possible.  I had all sorts of issues with installation until I did that.  Just to be sure, use the included test when you first boot the CD.

--Me

---

### Post by RomeReactor on 2008-06-13
HI. I don't use dual screens, so I don't know much about the issue. But you could try installing Ubuntu with only one monitor connected, and then if it installs correctly, connect the other one and configure them with the 'Screens and Graphics' application.

---

### Post by ON5MJ on 2008-06-14
Thank you to all of you.

1. Tamoneya: I don't remember having seen the option of safe boot at this level of installation. Just the language selection followed by the type of permanence of installation but it could be a clue.

2. canthus13: I have already seen a similar advice about the speed of engraving an ISO image on a DVD. Nevertheless, I also tried to install Ubuntu with a live CD from commercial origin (but a 32 bits version) that is supposedly clean. In both cases the sync of the image desappeared probably when the display passed to graphic.

3. RomeReactor: a double screen work space is just a single image shared on two pieces of hardware. Could be a copy of one another or a split work place as well. In the beginning the screens were OK and similar (excepted that the horizontal resolution was squeezed on the 19 " screen and spread on the 24" one). I will try your idea.

Clues 1 and 3 can be tested easily. If they don't work, I will try to redo the engraving. By the way, does somebody know how to control the fingerprint of an ISO file with XP. I don't see the hash reference on the belgian mirror of Ubuntu.

I have also seen somewhere for a previous version of Ubuntu that had the same problem that a possible solution could be to install an old working version and to upgrade it to a newest one.

---

### Post by tamoneya on 2008-06-14
the option used to be more obvious in 7.10 but in 8.04 it was moved to a more hidden area.  You have to select additional boot options.

---

