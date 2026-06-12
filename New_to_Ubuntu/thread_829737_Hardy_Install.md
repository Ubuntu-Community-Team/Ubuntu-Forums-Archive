---
title: "Hardy Install"
date: 2008-06-15
forum: New to Ubuntu
---

### Post by theRightNee on 2008-06-15
hey all,
trying to install hardy heron on a Sony Vaio PCG-9411 i managed to get working again (thank you God!), but when i try to install, i get to "Loading ACPI modules" and it stops loading

with gutsy i do not have this problem, so is it possible to use the hardy heron CD to upgrade gutsy?

thanks!

---

### Post by ukripper on 2008-06-15
> **theRightNee said:**
> hey all,
trying to install hardy heron on a Sony Vaio PCG-9411 i managed to get working again (thank you God!), but when i try to install, i get to "Loading ACPI modules" and it stops loading

with gutsy i do not have this problem, so is it possible to use the hardy heron CD to upgrade gutsy?

thanks!

There is a bug reported on launchpad.

Fix is to disable splash quiet during boot.

in terminal type this:
```
sudo gedit /boot/grub/menu.lst
```

and delete splash quiet so that kernel line ends at **ro**

---

### Post by theRightNee on 2008-06-15
the problem lies within the installation...how would i modify that?

---

### Post by ukripper on 2008-06-15
> **theRightNee said:**
> the problem lies within the installation...how would i modify that?

can you boot into ubuntu live cd?

---

### Post by theRightNee on 2008-06-15
ok i have isolated the problem
once i turn of the ACPI modules the live cd will boot normally, i have got 8.04 installed, but cannot boot...how do i boot into terminal?

---

