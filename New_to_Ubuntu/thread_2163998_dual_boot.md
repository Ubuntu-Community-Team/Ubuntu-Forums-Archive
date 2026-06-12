---
title: "dual boot"
date: 2013-07-20
forum: New to Ubuntu
---

### Post by nicbit on 2013-07-20
I dont know if this is the right section but here goes. I decided to install ubuntu 13.04 on my new Satellite computer. I  foratted and partitioned a usb as an ISO; I then went into the BIOS and  changed the boot order to enable me to boot onto the startup ISO. during  the installation, I almost formatted the entire HD (and almost erased  my thesis! LOL) but i managed to realize it in the nick of time. I then  decided to resize the windows partition and create a new partition for  ubuntu. During startup, to my dismay i could not boot onto windows 8!  (stupid windows 8 its all your fault lol.) Anyway, it obtained the  "unity reboot" script in which i could not find windows 8. I also  installed "Grub customizer" to attempt to change the default OS, but  could not find Windows 8 on the list. HELP I WANT BACK MY THESIS :'(  please help me

---

### Post by newb85 on 2013-07-20
Most likely, the problem is that Windows is set up in EFI and Ubuntu in Legacy partitioning.  In Ubuntu, install and run boot-repair.  It will most likely fix the problem, and if not, it will provide a lot of information helpful in troubleshooting.

---

### Post by oldfred on 2013-07-20
If thesis is at all important, I would make sure you have good backups. See the link in my signature on how to do that before installing with UEFI, but you can still do it.

+1 on newb85's suggestion.
Link to Boot-Repair.
       
Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

