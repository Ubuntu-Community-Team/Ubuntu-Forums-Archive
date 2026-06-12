---
title: "error showing at startup"
date: 2020-04-23
forum: New to Ubuntu
---

### Post by syedzeyad on 2020-04-23
when i'm starting my ubuntu following error is coming:

device descriptor read/64,error -32 (4 times)

/dev/sda5 contains a file system with errors, check forced.

device not accepting address 5,error -32

device not accepting address 6, error -32

unable to enumerate usb device

----other text--------

/dev/sda5: unexpected inconsistency;run fsck manually

--other text---

initramfs

---

### Post by CelticWarrior on 2020-04-23
At best this is indicative of correctable logical error in the aforementioned partition sda5 so it requires what the error message is telling you: *run fsck manually*.

---

### Post by syedzeyad on 2020-04-23
how can i run fsck manually?
thanks

---

### Post by CelticWarrior on 2020-04-23
[https://askubuntu.com/questions/353732/how-to-use-fsck-in-ubuntu](https://askubuntu.com/questions/353732/how-to-use-fsck-in-ubuntu)

---

