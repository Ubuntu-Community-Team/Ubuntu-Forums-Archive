---
title: "multiosboot"
date: 2012-02-07
forum: New to Ubuntu
---

### Post by VirtualMachine on 2012-02-07
Hi everybody,
Obviously i'm new.

To anybody who could help me with the following problem, many thanks!

I would like to install 3 os on my machine.
-win vista
-ubuntu 11.10
-lubuntu 11.10

I found instructions for doing this with grub-legacy (before ubuntu 9.04) on:  [https://help.ubuntu.com/community/MultiOSBoot](https://help.ubuntu.com/community/MultiOSBoot)
It doesn't work with the last os (lubuntu) Second Lubuntu OS
error: 15 File not found. Probably i'm missing something. The thing is i can't find anything regarding multiosboot using grub-2.

So please help me out!

---

### Post by Quackers on 2012-02-07
Welcome to UF :-)

Grub2 should sort itself out after installation. It should pick up all other operating systems and add them to the grub menu (as long as grub is installed to the drive (mbr) and not to a partition.

What operating systems are installed now?

---

### Post by hildenbrandsteven on 2012-02-08
Just out of curiosity, why not just install both desktop environments in Ubuntu. And the dual-boot with Vista is simple, both Linux installers will install grub which would solve the issue of bootloaders.

---

### Post by oldfred on 2012-02-08
If you are getting an error 15 that is from grub legacy. Grub2 has been the standard since 9.10, so did you follow some old instructions and install grub legacy 0.97?

This may fix your boot issues and if not run the boot_info_script it offers.

Boot Repair:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or post the link to a run of boot info script so we can see your exact configuration.

---

### Post by VirtualMachine on 2012-02-08
Thanks everybody,

@ Quackers: U are totally right, grub2 finds everything.
Now installed are WinVista, Ubuntu 11.10 and Lububtu 11.10.
And ofcourse its nice to be welcomed!

@ hildenbrandsteven: Indeed a good idea, i don't exacly know how to do that yet but it is probably more elegant running just one os with two desktop environments than to install the same os twice.
I didn't think of it.

@ oldfred: Yes i googled multiple os and ended up at:   [https://help.ubuntu.com/community/MultiOSBoot](https://help.ubuntu.com/community/MultiOSBoot)
This mentioned that using grub-legacy was the easiest way to boot more than 2 os, as far as i could find anyway. It seems to be outdated because the instruction doesn't work on my system. I will use the boot-repair next time i'm in trouble, but i already installed with grub-2 and it works excellent.Many thanks though!

Greetings to all:D

---

