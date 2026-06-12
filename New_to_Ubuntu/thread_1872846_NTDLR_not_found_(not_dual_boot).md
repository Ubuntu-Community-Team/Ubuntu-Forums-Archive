---
title: "NTDLR not found (not dual boot)"
date: 2011-10-31
forum: New to Ubuntu
---

### Post by richardi on 2011-10-31
Hi I've been using Ubuntu 64bit exclusively on this machine for nearly 2 years and just had a message at boot saying in German(!) NTDLR not found. I managed to boot into ubuntu by ctrl-alt-del then f3 and chose the hard disk to boot from. Grub then loads.

Google searches all mention windows and dual booting. This machine has never had anything but Ubuntu installed on it so dual booting is not an issue. I'd just like to be able to boot straight in as normal.

I also intend to upgrade from 10.10 to 11.10 in the next few weeks if that will make any difference.
Thanks in advance
Richard

---

### Post by Paqman on 2011-10-31
NTLDR is the Windows bootloader. Open a terminal and run:
```
sudo update-grub
```
This will force it to re-scan for operating systems, and hopefully it'll convince itself that you don't have Windows installed!

---

### Post by richardi on 2011-10-31
Thanks Paqman. Tried that and it made no difference. The problem is before grub loading. Any other ideas?

---

### Post by oldfred on 2011-10-31
Is BIOS set to boot a drive that still has the Windows boot loader in it? Your f3 is then changing to the correct drive?

---

### Post by richardi on 2011-10-31
oldfred - entered BIOS setup and changed hard disk to first in boot order priority (floppy and CD were before it) and it now works fine.
Many thanks. I guess if I want to run a live CD I need to change that in BIOS so CD goes first?

---

### Post by oldfred on 2011-10-31
I never change BIOS to boot CD or USB, I just use one time boot key (f12 on my system) looks like f3 on yours? If you do not have hard drive & correct hard drive first, it just takes a bit longer as it has to look for device & realize it is not bootable & then go to next device.

---

