---
title: "t420, pressing SHIFT for the GRUB menu doesn't work"
date: 2021-03-18
forum: New to Ubuntu
---

### Post by dave219 on 2021-03-18
hello team:

i am using old t420 for ubuntu 20.4. supposedly [CENTER][COLOR=#444444][FONT=&quot]pressing shift would bring up GRUB menu but in my case, it doesn't do anything.

how could i bring up GRUB menu as needed?

thanks

_dave[/FONT][/COLOR][/CENTER]

---

### Post by grahammechanical on 2021-03-18
What is a t420? Please will you give us more details about your hardware and whether this is a dual boot or not. Is Ubuntu the only operating system? If that machine has a UEFI motherboard then it is press and hold Esc.

The opprotunity for bringing up a grub menu is very short. Do you see a motherboard splash screen with its invitation to press certain keys to enter a settings utility? That is the time to press either shift or Esc as the case may be.

Why do you want to bring up the Grub menu. Is there something wrong with the installation of Ubuntu?

Regards

---

### Post by dave219 on 2021-03-18
sorry, it is not dual boot. the machine is lenovo t420 and ubuntu 20.4 is the only OS for this machine. yes it uses UEFI boot instead of legacy bios. i forgot password and try to get into single mode. btw, pressing Esc worked but what is next?

---

### Post by Impavidus on 2021-03-19
Select advanced options, choose to boot Ubuntu in recovery mode, at the next menu drop to a root shell. Remount the filesystem read-write and use passwd [username] to reset the password.

---

