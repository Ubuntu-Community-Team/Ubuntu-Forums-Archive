---
title: "How do I boot into Window by default?"
date: 2015-08-31
forum: New to Ubuntu
---

### Post by leoxie on 2015-08-31
I just installed Ubuntu 15.04 over Windows 7 and I do get the dual boot when I power on the system. By default, the system would boot into Unbuntu automatically after a few second, but my wife wants to keep using the Windows instead of the Ubuntu. How do I change the settings to set the default boot to Windows?

---

### Post by SeijiSensei on 2015-08-31
In the file /etc/defaults/grub you'll see a line that reads:
```
GRUB_DEFAULT=0
```
That tells grub to boot the first operating system in /boot/grub/grub.cfg.  (Unix-flavored systems like Linux generally start counting at zero.)  To change the default, count down to the Windows entry in the boot menu, then change "0" to the appropriate value.  For instance, if Windows is the third entry in the list you would set the default to "2".

You will need to edit this file as [root with sudo]("https://help.ubuntu.com/community/RootSudo").  You can do this by [opening a terminal]("https://help.ubuntu.com/community/UsingTheTerminal") (Ctrl+Alt+T), then typing:
```
sudo nano /etc/defaults/grub
```
You'll be asked to enter your login password, then you'll end up in the "nano" editor.  Make the change you need, then save it by holding down Ctrl and hitting "X" and entering "Y" when prompted.

---

### Post by oldfred on 2015-08-31
If you install Ubuntu over Windows, you erased Windows.
Did you really install side by side?

Post this:
sudo parted -l

---

### Post by SeijiSensei on 2015-08-31
The OP said he sees the boot menu, so I don't think he overwrote Windows.  He just wants to change the default OS.

I've installed Ubuntu over Windows in the past, and it never overwrote Windows.  Of course, I had repartitioned the drive beforehand to create free space for the Linux distribution.

---

### Post by leoxie on 2015-08-31
Thanks. I got it.

---

### Post by SeijiSensei on 2015-08-31
Great! Please mark this thread [SOLVED] from the "Thread Tools" menu at the top.

---

