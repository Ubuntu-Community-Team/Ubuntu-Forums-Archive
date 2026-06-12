---
title: "not booting"
date: 2008-05-11
forum: New to Ubuntu
---

### Post by estanton on 2008-05-11
after repairing GRUB this morning I can no longer boot. Instead i get dropped into a busybox shell. I'm running 8.04 with GNOME, however i recently installed KDE alongside and now when it boots up the blue Kubuntu splash screen comes up, which is a little odd. Any ideas?

---

### Post by diablo75 on 2008-05-11
> **estanton said:**
> after repairing GRUB this morning I can no longer boot....
Ok.
> and now when it boots up...
Wait, what?
> ...the blue Kubuntu splash screen comes up, which is a little odd. Any ideas?
When you say splash screen......  Could you just rephrase the original post?  You need to be more detailed.

---

### Post by dtrot55 on 2008-05-11
I had "kind of" a similar issue...I had to just change the boot sequence of my hard drives and it work'd...As in if I want to boot into Windows i had to put my windows partition as first boot...and vice versa for Ubuntu.

---

### Post by estanton on 2008-05-11
> **diablo75 said:**
> Ok.

Wait, what?

When you say splash screen......  Could you just rephrase the original post?  You need to be more detailed.

As per a previous [thread]("http://ubuntuforums.org/showthread.php?t=790177") I had to reinstall by boot loader (GRUB). After succesfully getting GRUB to work again the system is no longer booting up properly. I'm sorry I was being unclear before. This system begins to boot but does not finish. The splash screen comes up with the progress bar below and kinda hangs for awhile. I then get dumped in to the BusyBox shell and from there I'm a little stuck.

---

### Post by Yannick Le Saint kyncani on 2008-05-11
> **estanton said:**
> This system begins to boot but does not finish. The splash screen comes up with the progress bar below and kinda hangs for awhile. I then get dumped in to the BusyBox shell and from there I'm a little stuck.

Hi there,

You should edit the grub entry (at startup, in the grub menu, press "e"), replace "quiet splash" with "nosplash" and press "b" to boot. You will have to do this at each boot.

This way, you will be able to see the startup messages. It will still not work but you will be able to see what's going on.

Cheers.

---

