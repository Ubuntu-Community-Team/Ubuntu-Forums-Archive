---
title: "Error system"
date: 2018-03-14
forum: New to Ubuntu
---

### Post by awachens on 2018-03-14
Hi when i start session i get this error:

[https://imgur.com/a/z6bp7](https://imgur.com/a/z6bp7)

Regards !

---

### Post by mörgæs on 2018-03-14
Does this help?

[https://bugs.launchpad.net/ubuntu/+source/plymouth/+bug/927636/comments/51](https://bugs.launchpad.net/ubuntu/+source/plymouth/+bug/927636/comments/51)

---

### Post by awachens on 2018-03-15
Good morning !! Ofcourse I think this is the solution. i try and post again,

update-initramfs: deferring update (trigger activated)
update-rc.d: warning: start and stop actions are no longer supported; falling back to defaults
update-rc.d: warning: start and stop actions are no longer supported; falling back to defaults
Procesando disparadores para initramfs-tools (0.122ubuntu8.10) ...
update-initramfs: Generating /boot/initrd.img-4.10.0-28-generic



THX !

---

### Post by awachens on 2018-03-16
Hi error continue after use this command... 

What more can i do ?

Thx !

---

### Post by mörgæs on 2018-03-17
I don't know. What surprises me is that the bug has a heat of more than 1500 which suggests that it's common. Still I haven't experienced it in any of my installations. 

Time for broader experiments. How does a live boot of X/Lubuntu work?

---

### Post by awachens on 2018-03-19
Good morning, i use the command with SU and i think the problems it's solved..

Reggards !

---

