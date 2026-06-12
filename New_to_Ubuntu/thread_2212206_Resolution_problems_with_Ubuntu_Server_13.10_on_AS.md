---
title: "Resolution problems with Ubuntu Server 13.10 on ASUS Eee PC 1005P"
date: 2014-03-20
forum: New to Ubuntu
---

### Post by Nictac on 2014-03-20
I have installed Ubuntu Server on my netbook (the screen is broken so I use an external monitor connected via VGA) but cannot get it to display the console correctly.
The edges of the screen seem to be cut off and I cannot read the first 7 or so letters, anyone any ideas on how to fix this?

---

### Post by papibe on 2014-03-20
Hi Nictac.

Try this:

Edit the grub file:
```
sudo nano /etc/default/grub
```
Then look for a line like looks like this:
```
GRUB_CMDLINE_LINUX_DEFAULT=""
```
Copy and paste the line, comment one, and modify the other so it looks like this:
```
#GRUB_CMDLINE_LINUX_DEFAULT=""
GRUB_CMDLINE_LINUX_DEFAULT="splash vga=789"
```
Save the file and update grub:
```
sudo update-grub
```
Then reboot:
```
sudo reboot
```
Hope it helps. Let us know how it goes.
Regards.

---

### Post by Nictac on 2014-03-26
Hey,

tried that but it didn't work. Got it set up with openssh now so I can use putty from my desktop.

Thx for taking the time to respong though

---

