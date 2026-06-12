---
title: "Cant boot into my latest kernel!"
date: 2008-07-07
forum: New to Ubuntu
---

### Post by Spoken on 2008-07-07
i cant boot into my latest kernel which is 2.6.24-17

my computer automatically trys to boot into this one by default but when it gets to the loading bar screen.  the bar just goes back and forth forever.

right now im booted up into this same kernel (but in recovery mode)

so what do i need to do in order to get my computer to boot into this kernel normally once again.

---

### Post by Dr Small on 2008-07-07
Boot into recovery mode, edit /boot/grub/menu.lst and for the entry that is NOT the recovery mode, remove the "ro quiet" and "quiet" from the kernel lines so you can begin debugging the problem.

---

### Post by Spoken on 2008-07-07
ok, i did that and when it was spitting output at me during its "boot", it randomly stopped and near the bottom it said "driver "sr" needs updating -- please use bus_type methods"

and it never moved from there, so i had to do a hard shutdown and reboot into recovery again.

---

### Post by Dr Small on 2008-07-07
Anything you did beforehand that could have caused this? I don't know of anything off the top of my head that could be helpful. Maybe someone else will drop in with a solution.

PS. If you answer that first question, you void your warranty :D

---

### Post by Spoken on 2008-07-07
well i recently upgraded from 7.10 to 8.04, then after the upgrade, i got updates that required me to do a "partial upgrade", then after that, everything messed up.

---

### Post by fidamehran on 2008-07-08
Go to Synaptic and Package Manager and Search for Startup Manager. Install it. This is a very easy Graphical User Interface program that will let you manage what Kernel you will log in when Ubuntu starts. I use it. Top class.

---

### Post by fidamehran on 2008-07-08
With Startup manager you can also make Ubuntu load into previous stable Kernel versions. In my opinion, what kernel you boot into doesn't matter as long as its stable and not too old.

---

