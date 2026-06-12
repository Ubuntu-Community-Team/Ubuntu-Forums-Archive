---
title: "[SOLVED] triple boot xp vista ubuntu"
date: 2008-10-22
forum: New to Ubuntu
---

### Post by corkscrew on 2008-10-22
I have installed all 3 operating systems on 1 hard drive. xp then vista and then hardy heron. All are working.
However when i boot the machine I get the grub menu which lists xp , vista longhorn (loader) from this menu ubuntu boots fine. XP wont start i get a ntldr missing message.
If i select the vista option i get 2 choices of windows xp and vista and both work from there.

Is it not possible to do away with the vista loader and have grub do it all?

---

### Post by Dedoimedo on 2008-10-22
Hello,

As far as I know, the Vista bootloader "kills" the XP bootloader, which is what you get. I would suggest, for the sake of compatibility purposes and such, to remove the XP entry from the menu and let the Vista bootloader control XP.

After all, GRUB chainloads commands to the Vista / XP bootloader either way, so you're not losing/gaining anything here.

Dedoimedo

---

### Post by No-Neck on 2008-10-22
As far as I know, which isn't very far, no. It goes like this:

MBR &#8594; GRUB &#8594; NTLDR &#8594; Windows.

GRUB can't load Windows, only forward the computer to NTLDR.

EDIT: Beaten.

---

### Post by corkscrew on 2008-10-22
do you mean remove xp from the grub menu ? and how do i do that?

---

### Post by No-Neck on 2008-10-22
> **corkscrew said:**
> do you mean remove xp from the grub menu ? and how do i do that?
Open up a terminal and type:

```
sudo gedit /boot/grub/menu.lst
```

and find the 2 entries for Windows at the bottom, remove the one for XP, should look like this:

```
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1
```

EDIT: You don't need to remove the lines with #s in front.

While you're at it, you could change the name of Windows Longhorn/Vista to just Windows, or whatever tickles your fancy. :)

---

### Post by Dedoimedo on 2008-10-22
Hello,

Before you change GRUB, make sure you BACKUP!!!!!!!

```
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst-backup
```

Then, comment out the XP entry ... no need to actually delete the lines. Simply add # before the relevant entry lines.

Dedoimedo

---

### Post by Duck2006 on 2008-10-22
If you want one boot loader to load all the OS's then you may have to have some thing like EasyBCD to do it.

[http://neosmart.net/dl.php?id=1](http://neosmart.net/dl.php?id=1)

---

### Post by caljohnsmith on 2008-10-22
Corkscrew, it is certainly possible to do exactly what you want to do, namely boot XP, Vista, and Ubuntu directly from Grub without going through the Vista boot loader to boot XP. The process involves putting the XP boot files back in the XP partition and the Vista boot files back in the Vista partition. I just helped some else do exactly this about a month ago (he also had XP + Vista + Ubuntu) and we got it working perfectly. If you want help doing it, please first post:
```
sudo fdisk -lu
```
And let me know which partitions belong to XP and Vista. We can go from there if you like. :)

---

### Post by corkscrew on 2008-10-23
Thanks very much for the offer, I will keep it in mind and maybe take you up later on.
For the moment I installed Qgrubeditor, and removed xp entry, and old kernel and rescue entries to trim it down a bit.

---

