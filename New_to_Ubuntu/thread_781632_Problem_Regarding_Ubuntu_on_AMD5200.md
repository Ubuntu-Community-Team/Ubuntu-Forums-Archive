---
title: "Problem Regarding Ubuntu on AMD5200"
date: 2008-05-04
forum: New to Ubuntu
---

### Post by gaurishpatil on 2008-05-04
HI..
I have AMD 5200 64 bit proccesser.
I tried to install Ubuntu on my machine.
I tried Ubuntu7.10,Ubuntu 8.04 for  AMD.
I got follwing msg.after this the installation process stops.


Error:
[  45.080635]..MP-BIOS bug: 8254 timer not connected to IO-APIC
[  45.259695] Kernel panic-not syncing:IO-APIC + timer doesnot work! Boot with apic=debug and send report.Then try booting with the 'nopic' option




plz help me...

---

### Post by OldTimeTech on 2008-05-04
boot with the kernel options "noapic" and "acpi=no".
You can add these options to your /etc/grub.conf if successfull

---

