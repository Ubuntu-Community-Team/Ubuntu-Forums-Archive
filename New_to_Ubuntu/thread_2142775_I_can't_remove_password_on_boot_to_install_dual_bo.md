---
title: "I can't remove password on boot to install dual boot system"
date: 2013-05-06
forum: New to Ubuntu
---

### Post by aldiux76 on 2013-05-06
Hi, I do know my password on boot, but I need to get a dual boot system. I can't continue with the installation of the other OS, since the password on boot prevents the installer from running. I have changed OSs sometimes before, and this is the first time I encounter this problem.
I use a Dell N4030 with an Intel i3 processor. So, the question is how can I remove this password on boot?

---

### Post by MrSteve on 2013-05-06
try system settings > user account
and then change to auto log on (without password)

if that does not work, try
in a terminal

sudo gnome-control-center
press enter and then enter your password
change the log on settings from there  ...

---

### Post by nerdtron on 2013-05-06
> **aldiux76 said:**
> Hi, I do know my password on boot, but I need to get a dual boot system. I can't continue with the installation of the other OS, since the password on boot prevents the installer from running. I have changed OSs sometimes before, and this is the first time I encounter this problem.
I use a Dell N4030 with an Intel i3 processor. So, the question is how can I remove this password on boot?

Password on boot? You mean the password you set in the BIOS? There should be a setting there that would say about the boot password or protected boot or something along those lines. Since you know your password, you can easily disable it.

---

### Post by aldiux76 on 2013-05-31
In was able to remove the password from Bios, but not from the Ubuntu interface somehting. So, I re-installed the system from zero, since I was planning on doing at least another disk partition. Thanks for your help.

---

