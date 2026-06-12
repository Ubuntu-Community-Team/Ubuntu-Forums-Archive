---
title: "Hangs at loading module 'usb-storage' for 'USB Storage'."
date: 2008-06-22
forum: New to Ubuntu
---

### Post by Ujjay on 2008-06-22
Hello my Kunbuntu installation worked before, then I uninstalled it and tried again. It hangs at 90% loading module 'usb-storage' for 'USB Storage'. My windows XP cd hangs at setup is starting windows as well. One of my 6 usb ports on my motherboard doesn't work (if that's any help). Tried the alternate CD but it won't boot in my computer. I have:

ASrock alive nfp6 VSTA am2 mobo
2GB ram
80GB HDD
AM2 2.1GHZ

I suspect a harddrive issue but I'm not sure.

---

### Post by benerivo on 2008-06-22
If there's problems wih ubuntu and windows, then it's a hardware problem.
Can you enter the BIOS setup on boot, then perhaps disable usb hardware? Do you have a usb hard drive attached when trying to install?

---

### Post by Ujjay on 2008-06-22
I can disable but I need a usb mouse, otherwise I'll just have to wait and get a PS2 one.

---

### Post by benerivo on 2008-06-22
That's pretty unlucky, as you wouldn't need the mouse for an  alternate cd install. What about disabling USB 2 hardware in the BIOS and leaving USB 1 enabled (i know my BIOS allows this).
I might also try opening the pc case and unplugging the lead that connects to the faulty usb port?

---

### Post by Ujjay on 2008-06-22
This is weird. I disabled the usb, then turned off my computer. It wouldn't turn on without some fiddling. Then when it turned on, the POST laod screen was extremely slow (it did it before in a few seconds) the keyboard would work only some of the time, and my DVD burner wouldn't be recognized at all or barely work. WTF?

---

### Post by Ujjay on 2008-06-22
Well I got it fixed it was a bent pin in the DVDr drive. But now when I install I get this at 50%

Failed to copy files; faulty cd/dvd or harddisk.

The installer envountered an error in copying the files to the harddisk.

Errno 5 input/output error.

---

