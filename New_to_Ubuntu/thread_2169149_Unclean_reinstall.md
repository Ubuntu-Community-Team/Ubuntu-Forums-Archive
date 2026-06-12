---
title: "Unclean reinstall?"
date: 2013-08-20
forum: New to Ubuntu
---

### Post by GQDQALC on 2013-08-20
Hi again guys. 

I got my computer yesterday (I can post hardware details if needed but I don't think they're relevant) with windows pre-installed and I installed Ubuntu alongside it, no problems. Later I discovered I had my partitions reversed so Windows had too much room and Ubuntu had too little. I resized the partitions with GParted but then noticed that Ubuntu started freezing frequently, and it doesn't take a genius to figure the rest out. Anyway, I went ahead and booted from a liveusb and reinstalled Ubuntu onto the same partition it had been installed on, but when I rebooted GRUB2 showed me something strange:

At the top was Ubuntu, and two down was "Older Linux systems" or something like that; when I tried to boot Ubuntu, I got an error that said "An error occurred when mounting /boot/efi" and when I pressed skip I took me to the new system, but my touchpad didn't work. Even stranger is, when I rebooted and tried the "Older Linux systems" it took me to my old install, which I had assumed was wiped during reinstallation. What's happening?

Thanks.

---

### Post by Quackers on 2013-08-20
It seems certain that you have installed Ubuntu twice.
Firstly I would make sure that Windows still boots ok from the grub menu entry (assuming there is one).
If it boots ok I would suggest that you run the Ubuntu live cd and select try Ubuntu. Once the desktop loads I would run gparted (can't remember if that's installed or not in the live cd desktop) and view the partitions. I suspect there will be two Ubuntu partitions and possibly 2 swap partitions. I think it may be best to scrap those partitions and leave the free space so that you can do a fresh install of Ubuntu in that. This should also solve your size problem for Ubuntu.

---

### Post by GQDQALC on 2013-08-20
OK, I tried booting from a liveusb and looking at it in GParted but I only see one Ubuntu partition and one swap. Very odd. Should I delete those partitions then?

EDIT: Windows is unaffected; I was afraid I had overwritten Windows by mistake too at first, but thankfully no. OK, so I tried booting up and investigating more at "Previous Linux Versions" (the Older Linux Systems I was talking about). If I click that I'm taken to a new GRUB screen with the usual options, Ubuntu and Ubuntu advanced for recovery (no windows options). I click Ubuntu and it boots normally, but it wasn't my old system since several programs I installed are no longer installed - it seems to be the fresh install but Ubuntu was nice enough to save my /home folder. Less frantic now, but what is the meaning of the efi boot error when I try to access it from the main screen, and "Previous Linux Versions" - what's that about? (I should note that after I reinstalled I ran boot-repair recommended from a liveusb as well, forgot to mention that)

Thanks

---

### Post by penelope2 on 2013-08-21
I'm new but Ubuntu Boot Repair Cd  saved my computer OS on several occasions.  If I were you I would burn a copy of it.  Stick it in the CD Drive and be prepared to wait a few minutes for it to start (it is slow but it will start). Gparted is there  (lower left corner of screen menus), you can let it remove an OS if you need to do that then run boot repair option.  It  will fix grub and your WIndows boot problem if you have one (it fixed mine)>  This has been a definate have to have CD !!  Good Luck!

---

### Post by Mark Phelps on 2013-08-21
> EDIT: Windows is unaffected; I was afraid I had overwritten Windows by mistake too at first, but thankfully no. 

Are you saying this because the Windows partitions appear to be intact? Or, are you saying this because, as suggested, you actually booted into Windows and confirmed it still boots and runs OK?

If it's the former, then you really need to do the latter -- as resizing Windows filesystems with GParted sometimes leads to filesystem corruption -- something you would only detect if you actually tried to use Windows after the resizing.

---

