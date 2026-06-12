---
title: "Computer gives no such device error"
date: 2011-12-04
forum: New to Ubuntu
---

### Post by rodk98 on 2011-12-04
From a complete newbie to Linux and Forums.

Got an aging HP Pavilion with XP OS and have tried to install the recent version of Ubuntu Linux on a separate USB HD. All seemed to be OK until I tried to reboot the computer when I got the message:

No such device :- 1aafc48b-a585-4680-98a3-73aba42e8f57

grub rescue>

This happens even if the USB HD is attached or not so it makes booting to XP tricky as I have to go via the recovery disc (not really a problem as system is clunky anyway).

Anybody with any ideas I'd be grateful. I may not get back to you quickly but you have my thanks upfront.

---

### Post by sanderd17 on 2011-12-04
The problem is probably that the mbr of your internal disk is used.

So the mbr searches for Grub, which is on your other disk, but can't find it in a lot of cases.

To repair this, you need to repair the windows mbr with a windows repair disk, and reinstall Grub again to the mbr of your external disk.

Now a bit of elaboration:

[LIST]
[*]MBR stands for Master Boot Record. It's a physical part of your hard disk, and every time you boot your computer, the code on the MBR is the first one to be excecuted.
[*]GRUB stands for GRand Unified Bootloader, that's a program that let's you choose the OS.
[/LIST]

So the bios picks the mbr of your primary hard drive and executes the code on it.

The label you see (1aafc48b-a585-4680-98a3-73aba42e8f57) is the name of a hard drive (probably your external one).

---

### Post by rodk98 on 2011-12-04
Many thank for that. I think I should have left things well alone!!

---

### Post by sanderd17 on 2011-12-04
> **rodk98 said:**
> Many thank for that. I think I should have left things well alone!!

You can only learn by trying, how do you think I know it ;)

---

### Post by Rubi1200 on 2011-12-04
Hi and welcome to the forums rodk98 :)

I would want to see the results of the boot info script just to make sure there are no surprises before you go ahead and follow the advice just posted (which is good advice by the way).

There is a link at the bottom of my post with instructions.

Thanks.

---

