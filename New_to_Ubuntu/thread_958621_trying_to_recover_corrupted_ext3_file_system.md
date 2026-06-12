---
title: "trying to recover corrupted ext3 file system"
date: 2008-10-25
forum: New to Ubuntu
---

### Post by exilio3000 on 2008-10-25
Hello all,

I had an accidental "cold" shutdown and could not boot again after that. I am trying to follow a tutorial about disk recovery. So far, I've booted into recovery mode as root, but when i try to:

umount /dev/sda3

I can't seem to unmount the partition - after typing:

mount

i get:

/dev/sda3 on / type ext3 (rw, errors=remount-ro)

That means it is still mounted, no?

---

### Post by bodhi.zazen on 2008-10-25
Boot to a live CD to perform file system maintenance.

---

### Post by exilio3000 on 2008-10-25
thankyou bodi for that suggestion

could anyone suggest a good tutorial on livecd system recovery. Also, I've been using Feisty, which is now unmaintained - will I have problems with my wireless (the Orinoco driver is what is currently running wifi) if I move to Hardy?

thanx again, 
exilio

---

### Post by bodhi.zazen on 2008-10-26
It depends on the problem.

I would start here : [https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)

---

