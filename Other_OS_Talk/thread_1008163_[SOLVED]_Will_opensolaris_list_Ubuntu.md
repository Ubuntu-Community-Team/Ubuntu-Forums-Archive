---
title: "[SOLVED] Will opensolaris list Ubuntu?"
date: 2008-12-11
forum: Other OS Talk
---

### Post by cl333r on 2008-12-11
Hi,
Does anyone know whether OpenSolaris 2008/11 after installation detects Ubuntu (my main OS) and appends it to the grub menu list?

---

### Post by Antman on 2008-12-11
Sorry... I have no clue. But, have you tried installing [Virtualbox]("http://www.virtualbox.org") and loading OpenSolaris in a vm session? It's an awesome way to test an OS without screwing up your main box.

---

### Post by cl333r on 2008-12-11
Thanks, I have installed it (a few days ago) on my 2nd computer which is a test machine, I couldn't get a few things working and I thought perhaps on this one it will work. On that machine I had no OS to care about, but this one is my "working horse" so I'd like to know this before installing it.. I just got stroke by an idea, I'll install Ubuntu on that one and then OpenSolaris and see what happpens.. will take like 1-2 hours though.
PS: On that computer I had windows and it actually got listed, but I dunno whether Ubuntu is detected as well. Gonna check now.

---

### Post by cmay on 2008-12-11
no it will not. it says so in the install instructions . i use open-solaris 2008.11 as the only system on my new computer and it runs great but i have never tried to dual boot with linux.

---

### Post by cl333r on 2008-12-11
Well I just finished the experiment and you're right. It doesn't. I guess I'll wait for better days since trying out ZFS and DTrace isn't that important to me.

---

### Post by namegame on 2008-12-11
I've never used OpenSolaris so YMMV.

You should be able to manually edit grub, lilo, etc, to include your Ubuntu partition.

---

### Post by cardinals_fan on 2008-12-11
I seem to remember it detecting my Linux partition, though it didn't add it to GRUB.

---

