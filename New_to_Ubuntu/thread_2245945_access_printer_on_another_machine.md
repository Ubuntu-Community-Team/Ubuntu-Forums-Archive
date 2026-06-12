---
title: "access printer on another machine"
date: 2014-09-27
forum: New to Ubuntu
---

### Post by snowmobiler on 2014-09-27
I am trying to access from my laptop, the USB printer I put on my pc. Is that possible w/Ubuntu? I thought it had to do with setting the right host (PC name), but that didn't seem to work. In the printer preferences, the shared box is checked but it does say "not published, see server settings", but I don't see where to change something like that. I've done this numerous time w windows PCs.

---

### Post by stalkingwolf on 2014-09-27
yes it can be done.  what version of buntu ar you using?  are you networking from a buntu machine or windows machine?   at times it can be tricky going from a windows machine to buntu, or at least last time i did it.

---

### Post by snowmobiler on 2014-09-27
Its a Windows Network. But i have Ubuntu 14.04 on both the laptop and the PC where the printer is located.

---

### Post by Vladlenin5000 on 2014-09-27
In the print server PC:

1. At System settings > Printers select the server settings from the server menu and there you want shared printers published (other computers in the network won't see it otherwise). Other options depend on what you want to do and what privileges you want to concede to remote printing. 
2. Right-click the printer itself and make sure it is shared.

---

### Post by snowmobiler on 2014-09-27
unfortunately under printers, and settings, there is no server option. It is connected as local host via USB. Yes, its listed as shared, just can't figure out how to make it visible.

---

### Post by deadflowr on 2014-09-27
Try using cups.
open a browser and enter
```
localhost:631
```
go to the section marked Adiministration
then in the right side check the entry for
Share printers connected to this system.
Apply changes, you simply use the username and password of the machine/os you are on.

See what happens next.

---

### Post by snowmobiler on 2014-09-27
> **deadflowr said:**
> Try using cups.
open a browser and enter
```
localhost:631
```
go to the section marked Adiministration
then in the right side check the entry for
Share printers connected to this system.
Apply changes, you simply use the username and password of the machine/os you are on.

See what happens next.

That worked! Awesome. Learning something everyday.

---

