---
title: "Cannot remove grub"
date: 2011-10-19
forum: New to Ubuntu
---

### Post by hyperAura on 2011-10-19
Hi,

I recently setup a new machine and I installed Ubuntu on it. Later on I installed Windows in order to have a dual boot but as soon as I opened the machine it went straight to Ubuntu. No option for loading windows.

I then decided to remove everything and install them the other way round (first Windows then Ubuntu) as I did it in the past and it worked. 

The problem now is that I did format my hard drives and when I turn on the machine I get

error:unknown filesystem
grub rescue

How can I remove the grub completely in order to install them the other way round?

---

### Post by Paqman on 2011-10-19
You shouldn't need to remove Grub, just boot up into your Windows install disk.

---

### Post by hyperAura on 2011-10-19
I installed Windows again and I get the same message. For some reason Windows is not being added in the list. The machine is trying to load ubuntu even after formatting my hard drive.

---

### Post by Mark Phelps on 2011-10-19
The invocation for GRUB is stored in the disk's Master Boot Record (MBR) -- which is NOT overwritten when you reformat the drive.

You need to boot from a Windows CD and replace the MBR.

---

### Post by hyperAura on 2011-10-19
Thanks guys! Thanks for the explanation Mark! :)

---

### Post by Paqman on 2011-10-19
Alternatively, when you reinstall Ubuntu it will reinstall Grub, wiping out any previous settings.

---

