---
title: "uninstall question"
date: 2016-01-13
forum: New to Ubuntu
---

### Post by james_grose2 on 2016-01-13
I bought an hp 6730b laptop that came with Linux mint.  I'm thinking of installing Ubuntu.  If I don't like it, how do I get rid of it later without losing Mint.

---

### Post by sandyd on 2016-01-13
A few options:

1. Dual Boot
Ubuntu installer can handle this as long as you have enough partitions left (only on MBR).
If you don't like Ubuntu, simply delete the Ubuntu partitions from mint, and run boot-repair to install boot loader back on mint.

2. Run on VM
If you just want to try it out, you can use virtualbox or similar to run it. Uninstalling is easy as deleting the VM.

3. Run on external USB.
Ubuntu can be installed to USB as well with persistent storage, Uninstalling is easy as simply wiping the USB.

---

### Post by james_grose2 on 2016-01-14
is boot-repair an application. do I run it from terminal, or what??  Thanks for the help!!

---

### Post by Bucky Ball on 2016-01-14
See here:

Get Boot Repair:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

Yannbuntu's thread:
[http://ubuntuforums.org/showthread.php?t=1769482](http://ubuntuforums.org/showthread.php?t=1769482)

---

