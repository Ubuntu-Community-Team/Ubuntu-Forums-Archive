---
title: "Mount New hard drive from old Linux box"
date: 2008-09-07
forum: New to Ubuntu
---

### Post by lance bermudez on 2008-09-07
My old linux box mother board has problems and can not find my hard drives. So I have put them in my new linux box and they work just fine if you are root. I want to use them without have to use gksu nautilus to move files around. Attached is my fstab file I need the mount of 40.0 and 59.6 fixed so that i do not have to use root.

---

### Post by Xiong Chiamiov on 2008-09-07
Hmm, I haven't worked out some things with graphical text editors yet (new install), and I don't want to go find that file in my temporary storage, but I should be able to help you.

What you need to do is to change the owner and permissions of those drives.  Take a look at my post [here]("http://ubuntuforums.org/showthread.php?t=913228").  If they are ntfs drives, I believe you have to add umask=022 or some such to the options in your fstab.

---

