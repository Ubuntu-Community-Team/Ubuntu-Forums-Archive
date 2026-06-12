---
title: "Can't Get Rid of Windows Bootloader"
date: 2008-07-22
forum: New to Ubuntu
---

### Post by xItachi on 2008-07-22
For some reason I can't replace the Windows bootloader with the Linux one.  I booted Ubuntu off the cd and went to grub and did

```
find /boot/grub/stage2
root (hd0,0)
setup (hd0,0)
```

It says that the setup finished successfully, but when I reboot my computer it still goes into the Windows bootloader.

Here is the history of my computer:

First I had Windows only, then I later I made a new partition.. Ubuntu was hd2, and Windows was hd1.  Then I decided to delete my Windows partition so I only had Ubuntu on hd2.  Yesterday I decided to create a Windows partition because I wanted to play a game, but I created the Windows partition *after* the Ubuntu partition, so I'm not sure if it's hd1 or hd3.  But after I installed Windows on this partition it seems that I cannot setup grub loader and replace it with the Windows bootloader.  I used to be able to do this all the time.  Any ideas?  Thanks!

---

### Post by Ptero-4 on 2008-07-22
You might want to use the super grub disk, it allows to restore grub in this type of cases.

---

### Post by Yuki_Nagato on 2008-07-22
I too would recommend the Super GRUB Disk.

However, one of my rigs (the family one) is set to "hide" the GRUB menu and default boot into Windows.  Cause the rest of the family is comfortable with that.

It looks exactly like the Windows Boot with that little blinking cursor.

I have to press "esc" in order to see the boot menu, when that little cursor pops up.

---

### Post by L815 on 2008-07-22
Did you run those as root? (sudo su)

---

### Post by xItachi on 2008-07-22
Thanks! I managed to fix it.  I booted into my Ubuntu partition and changed menu.lst so that Ubuntu is (hd0,0) and Windows XP is (hd0,1) and it works perfectly fine :)

---

### Post by ajmorris on 2008-07-22
> **xItachi said:**
> For some reason I can't replace the Windows bootloader with the Linux one.  I booted Ubuntu off the cd and went to grub and did

```
find /boot/grub/stage2
root (hd0,0)
setup (hd0,0)
```

Hi there,
glad to see you have fixed your problem by another method, but for future reference, that command you ran is not what you would want to do. That installs grub to the partition (hd0,0). Running root (hd0,0) specifies that you would like to use the grub files from that partition, then you run setup (hd0). hd0 is the MBR, and this will overwrite the mbr with grub, so that you boot into the grub bootloader instead of the windows one :)

AJ

---

### Post by xItachi on 2008-07-25
Oh okay thanks :) I was confused about that a while ago when I was installing Ubuntu and never got it clarified haha

---

