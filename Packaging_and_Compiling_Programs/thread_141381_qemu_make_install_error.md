---
title: "qemu make install error"
date: 2006-03-08
forum: Packaging and Compiling Programs
---

### Post by carverj on 2006-03-08
Am trying to install qemu and have encountered many difficulties as I am new to compiling from source. Regardless, I managed to configure successfully (fingers crossed), So I tried to continue with sudo make install and got the following
FATAL error
Code:

make[1]: Entering directory `/home/jeremy/temp /qemu-0.8.0/arm-softmmu' install -m 755 -s qemu-system-arm "/usr/local/bin" make[1]: Leaving directory `/home/jeremy/temp /qemu-0.8.0/arm-softmmu' cd kqemu ; ./install.sh root@UBUNTU:/home/jeremy/temp/qemu-0.8.0# sudo modprobe kqemu FATAL: Error inserting kqemu (/lib/modules/2.6.12-10-386 /misc/kqemu.ko): Invalid module format



Do you know what is wrong?

---

### Post by Stealth on 2006-03-08
Hmm...have you checked out [this guide here]("http://www.ubuntuforums.org/showthread.php?t=39513")? Maybe you can find something in there...

---

### Post by carverj on 2006-03-09
yup, yup. friend told me to give automake a try!
anyone tried this? should I give a go?

---

### Post by adamkane on 2006-03-14
I tried to put together the simplest ways to install QEMU and KQEMU.
[http://www.ubuntuforums.org/showthread.php?t=142191]("http://www.ubuntuforums.org/showthread.php?t=142191")

---

