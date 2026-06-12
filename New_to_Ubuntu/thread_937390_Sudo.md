---
title: "Sudo"
date: 2008-10-03
forum: New to Ubuntu
---

### Post by Tex786 on 2008-10-03
Hi

I am new to Ubuntu (Linux in general) and I was wanting to know if someone could tell me about this sudo stuff.

What are some comands that can be used?

Thanks

---

### Post by eolson on 2008-10-03
Essentially sudo gives you root privileges from the command line.   Commands available are extensive.  Here are most of them

[http://www.ss64.com/bash/](http://www.ss64.com/bash/)

well, maybe not most, but alot.

---

### Post by drs305 on 2008-10-03
Here is the ubuntu community documentation:
[RootSudo]("https://help.ubuntu.com/community/RootSudo")

Added:
Essentially, normal uses are prevented from altering system files or running apps that might do the same. The first user designated on the system, by default, is able to temporarily gain the ability to do so by appending commands with 'sudo' for command line operations and "gksudo" for graphical applications.

You can append almost any command with "sudo" or "gksudo" but that doesn't mean you should. For instance, your apps maintain your configuration files in your home folder. If you suddenly decide to run an app such as firefox as root, it will write the configuration files to the system instead of to your personal settings. (Note - you don't want to do this.)

Don't use root unless you have to. Common tasks sometimes requiring admisitrative powers include copying/deleting/renaming files (sudo cp/rm/mv) into system folders, installing/uninstalling applications via the command line (sudo apt-get install or sudo aptitude install) or synaptic (it will ask for your password), modifying your fstab or grub menus (gksudo gedit /etc/fstab or /boot/grub/menu.lst), and some system inspection commands (sudo fdisk -l).

---

### Post by Dr Small on 2008-10-03
+1 to drs305's explanation.
'sudo' can also be broken down to say, '**S**uper **U**ser **DO**'

---

