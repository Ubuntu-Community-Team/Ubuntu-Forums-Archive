---
title: "Grub Fails on first boot after install"
date: 2008-08-30
forum: New to Ubuntu
---

### Post by henryrhenryr on 2008-08-30
Hi

I just got Ubuntu 8.04 onto my Thinkpad i1400 - it's pretty old but functioning and the installation has just finished.

I get to "Grub loading, please wait..." and it stops.

One potential cause is that the BIOS has an error with the clock - something about the battery:
CMOS Battery Bad...Real time clock error.

But the machine previously has Win98 and it was booting ok.

Does anyone know what would cause GRUB to freeze like this?

Thanks!

Henry

ps. I've tried...

- reinstalling grub on master boot record using recovery disk

---

### Post by gmxgeek on 2008-08-30
A bad CMOS battery is not usually a good sign. I would start by replacing it, and see if the issue resolves itself. If not, post back here.

---

### Post by GepettoBR on 2008-08-30
There are many reasons why it could be freezing, but what's more important is that you fix it. Can you still boot a LiveCD? If so, enter a terminal in the LiveCD and type the following: 
```

sudo grub
find /boot/grub/stage1 #This will return a message saying "hd**x**,**y**", 
             #where x and y are numbers. Use these numbers when I say "hdx,y".
root (hdx,y)
setup (hd0)
quit
```

This is assuming you want to install GRUB to your MBR (Master Boot Record). If you don't know what that means, then you can follow my instructions safely.

---

### Post by henryrhenryr on 2008-08-30
> **GepettoBR said:**
> There are many reasons why it could be freezing, but what's more important is that you fix it. Can you still boot a LiveCD? If so, enter a terminal in the LiveCD and type the following: 
```

sudo grub
find /boot/grub/stage1 #This will return a message saying "hd**x**,**y**", where x and y are numbers. Usethese numbers when I say "hdx,y".
root (hdx,y)
setup (hd0)
quit

This is assuming you want to install GRUB to your MBR (Master Boot Record). If you don't know what that means, then you can follow my instructions safely.

```

Thanks for replies.  I will try the CMOS battery next but I did manage to get the recovery disk to boot to a command line.

The output is:

```

sudo grub
Probing devices to guess BIOS drives.  This may take a long time.
Error opening terminal: bterm.

```

bterm?

I had a look at menu.lst and it looks correct.  I also tried putting grub on a floppy.  It also froze.

Next try...cmos battery...

---

