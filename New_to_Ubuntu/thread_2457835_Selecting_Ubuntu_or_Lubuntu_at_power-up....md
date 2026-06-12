---
title: "Selecting Ubuntu or Lubuntu at power-up..."
date: 2021-02-10
forum: New to Ubuntu
---

### Post by Innernet on 2021-02-10
Greetings.
After using Ubuntu many years; installed Lubuntu alongside recently and am happy so far.

A ~50/50 system suggested partition was created when installing Lubuntu 'alongside' ; I would think I should have the option to boot from one or the other at power-up.  See nothing  :(
How to select the flavor at power-up ?

---

### Post by yancek on 2021-02-10
It should have run update-grub after the installation of Lubuntu.  Are you able to boot into both? or just Lubuntur?  Do you not see a menu on Boot?  Is this an EFI or a Legacy install?  If you are only able to boot Lubuntu and you run sudo update-grub from the installed Lubuntu, you should see an option for the original Ubuntu. If updating grub doesn't resolve the problem, try posting the output of:

> sudo fdiks -l

Have you looked at the /boot/grub/grub.cfg file to see if there are entries for Ubuntu?

---

### Post by Innernet on 2021-02-11
Thank you yancek. Solved.  
But your sudo fdiks -l does not exist.

---

### Post by Impavidus on 2021-02-12
That's because there's a typo.```
sudo fdisk -l
```
But you solved it already, so don't mind.

---

### Post by ActionParsnip on 2021-02-12
Can you please post the fix. It may help others with a similar issue

---

