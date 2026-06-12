---
title: "reformat needed to install Ubuntu and Win 7"
date: 2011-11-21
forum: New to Ubuntu
---

### Post by Brianret on 2011-11-21
[SIZE=2]In my own inimitable fashion I have cobbled things up big time and I now need to start from scratch. It goes like this - I have a 1tb hard drive on which I have Windows 7 and Ubuntu 11.10 and, the whole thing is a complete shambles! I have decided to start again and reinstall Windows and Ubuntu 50/50.[/SIZE]
[SIZE=2]I need to format the complete drive to give me this opportunity but I am unsure as to how to do this, I have tried Gparted but this does not tell me how to wipe a complete drive.[/SIZE]
[SIZE=2]Any advice?[/SIZE]

---

### Post by coffeecat on 2011-11-21
> **Brianret said:**
> [SIZE=2]I have tried Gparted but this does not tell me how to wipe a complete drive.[/SIZE]
[SIZE=2]Any advice?[/SIZE]

Easiest and quickest way is to write a new partition table from the Gparted "Device" menu. Then you have an effectively blank, unformatted drive with no partitions.

Install Windows first making sure the partitions the installer creates are the size you want. Once Windows is installed to half of the drive and working, you can create your Ubuntu partitions with Gparted from the luve Ubuntu CD and install Ubuntu to them.

**EDIT**: forgot one thing. If you are using Gparted from the live CD to blank your drive, right-click on any swap partitions and choose "swapoff" first.

---

