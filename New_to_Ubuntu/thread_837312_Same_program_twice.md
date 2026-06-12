---
title: "Same program twice?"
date: 2008-06-22
forum: New to Ubuntu
---

### Post by Hillside on 2008-06-22
I tried using Linux for the first time 22 hours ago, I have installed Ubuntu Studio on dual boot with another operating system that begins with 'W' (sorry).
Earlier, when I was receiving some automatic updates, I lost power. When I restarted, I chose 'recovery mode' because I thought that was the right thing to do. Everything worked fine but now when I log on, I appear to have two Ubuntus to choose from. 
Sorry if this is a silly question, but what should I do about this?
Login reads:-

Ubuntu 8.04, kernel 2.6.24-19-rt
Ubuntu 8.04, kernel 2.6.24-19-rt (recovery mode)
Ubuntu 8.04, kernel 2.6.24-19-rt
Ubuntu 8.04, kernel 2.6.24-19-rt (recovery mode)
Ubuntu 8.04, memtest86+
Other operating systems:

(etc..... you know what else I have there!)

---

### Post by Kevbert on 2008-06-22
Just run
```
sudo cp /boot/grub/menu.lst /boot/grub/menu.old
```
to back up the old menu version to menu.old.  Then 
```
sudo gedit /boot/grub/menu.lst 
```
and delete the lines you don't want.  Save and exit and then reboot.

---

### Post by _sphinx_ on 2008-06-22
You should chose the first one, others are just old kernels in case your new kernel doesn't works properly.
You can remove them from synaptic. But you should keep your latest kernel if it works fine for you.

---

### Post by cariboo on 2008-06-22
You don't have to apologize for using Windows, I usually recommend that you dual boot until you are absolutely sure that you are happy with a Linux distribution, until you have everything working properly it is always a good idea to have internet access to check documentation and download drivers for your hardware if it is available. It is always a good idea to keep at least one older kerenl just in case there is a problem with the new one.

Jim

---

