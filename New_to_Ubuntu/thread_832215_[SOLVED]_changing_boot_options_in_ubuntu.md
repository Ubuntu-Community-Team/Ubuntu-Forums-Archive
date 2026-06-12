---
title: "[SOLVED] changing boot options in ubuntu?"
date: 2008-06-17
forum: New to Ubuntu
---

### Post by Azeem1991 on 2008-06-17
hi, i want to install XP on a separate hard drive, for gaming etc, and dont know how to boot from the cd...
it automatically boots into ubuntu which i dont want..

---

### Post by rune0077 on 2008-06-17
You'll probably need to change your bios-settings to boot from the disc-drive before the hard-drive.

---

### Post by ChildOfMana on 2008-06-17
You need to go into your computer's BIOS and alter the Boot Order (sometimes also referred to as 'Boot Sequence' or just simply 'Boot') and set it to boot from CD-ROM. Then restart your computer with the disc in the drive and it should boot off the CD rather than the Hard Drive.

How you enter your BIOS will depend on what BIOS your motherboard uses but the most common keys are usually [DEL] or [F2]  (keep tapping them when your computer first powers up).

One thing though - if you've already got Ubuntu installed it's probably a bad idea to install XP second as NTLDR (the Windows Boot Loader) will overwrite GRUB (the Linux Boot Loader) and that can be tricky to fix if you don't know what you're doing.

---

### Post by Azeem1991 on 2008-06-17
right..even if XP is on a separate hard drive?

---

### Post by rune0077 on 2008-06-17
Well, the trouble is that it has nothing to do with what OS you're using. Your BIOS is on your computer even if nothing else is installed on it. How to access it depends on the manufacturers of your computer, so if you don't know you'll have to read the manual, contact the manufacturers or google it (try googling "accessing the BIOS on <insert brand/model of your computer>").

Once you're in the BIOS you should be able to find a boot-order list, and then just make sure that your cd/dvd-drive is at the top of the list.

---

### Post by Azeem1991 on 2008-06-17
no no, ive got the booting thing sorted, i just thought it might work diffeently if ubuntu is installed, im asking if the ntldr erases grub even if theyre both on separate hds..

---

### Post by ChildOfMana on 2008-06-17
> Quote:
Originally Posted by Azeem1991 View Post
right..even if XP is on a separate hard drive?
Well, the trouble is that it has nothing to do with what OS you're using. Your BIOS is on your computer even if nothing else is installed on it. How to access it depends on the manufacturers of your computer, so if you don't know you'll have to read the manual, contact the manufacturers or google it (try googling "accessing the BIOS on <insert brand/model of your computer>").

Once you're in the BIOS you should be able to find a boot-order list, and then just make sure that your cd/dvd-drive is at the top of the list.

I think Azeem1991 means after he's sorted the Boot Sequence out, and is referring to installing XP.

> **Azeem1991 said:**
> right..even if XP is on a separate hard drive?

As far as I know NTLDR will write to the master (or primary) hard drive, regardless what drive XP itself is installed to.

Someone correct me if I'm wrong on that one though.

---

### Post by rune0077 on 2008-06-17
> **Azeem1991 said:**
> no no, ive got the booting thing sorted, i just thought it might work diffeently if ubuntu is installed, im asking if the ntldr erases grub even if theyre both on separate hds..

Sorry, you changed your post while I was replying to it :)

---

### Post by Miljet on 2008-06-17
Since you are installing Windows on a separate drive, it might be a good idea to disconect your Ubuntu drive during installation. That will preserve your Ubuntu installation. It will then be a simple matter to add the Windows boot information to your /boot/grub/menu.lst file.

---

### Post by BlackDragonBE on 2008-06-17
Burn a cd with [Super Grub Disk]("http://www.supergrubdisk.org/"), then read/print [this]("http://www.supergrubdisk.org/wiki/Howto_Fix_Grub"), then after you installed xp, boot from the super grub disk cd and follow the instructions.

Enjoy

---

### Post by Azeem1991 on 2008-06-17
got it..kind of... haha ok, here goes nothing then, ill disconnect the ubuntu drive first of all, then install xp, then come back here when done, and ask for further help writing this boot optiony stuff to menu..

---

### Post by ChildOfMana on 2008-06-17
Good luck.

You'll probably find its easier than it looks :)

---

