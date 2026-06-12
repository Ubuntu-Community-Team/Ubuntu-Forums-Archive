---
title: "Removing Grub"
date: 2014-06-28
forum: New to Ubuntu
---

### Post by Quarkrad on 2014-06-28
I installed Ubuntu on a newly created partition (as a dual boot machine) for a friend but it didn't work for them so I have been asked to put their machine 'back to how it was' - i.e. just win7.  I do not intend to get rid of the Ubuntu partition or the OS but to just remove grub and repair the win 7 boot loader - like a lot of machines my friend does not have the Windows install CDs.  Can I remove grub and repair the win7 boot loader using the Boot-Repair CD?

---

### Post by coffeecat on 2014-06-28
So long as Windows is still booting OK, you can rewrite the first 440 bytes in the mbr to restore normal Windows booting using an Ubuntu live CD. You can even boot into the installed Ubuntu and do this with one of the methods described in the link below. Or to answer your question, yes, Boot Repair CD will do the job just fine.

Useful link:

[https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader](https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader)

---

### Post by LastDino on 2014-06-28
Not even recovery CD? I haven't tried with Boot-repiar specifically, so I wont comment there, but if you've recovery CD, you can boot into it and simply type 
```

bootrec /fixmbr
```

[FONT=arial]If you can't create recovery CD, then try using Lilo, you can boot into Ubuntu DVD/USB live and install Lilo on it.[/FONT]

Then open terminal and enter this
```

sudo lilo -M /dev/sda mbr
```

[FONT=arial]Note: Judging by how you're keeping Ubuntu partition, if you plan to boot it later you may need easyBCD. If grub is not an option.

Damn! Ninja cat.
[/FONT]

---

### Post by Bucky Ball on 2014-06-28
> **coffeecat said:**
> So long as Windows is still booting OK, you can rewrite the first 440 bytes in the mbr to restore normal Windows booting using an Ubuntu live CD. You can even boot into the installed Ubuntu and do this with one of the methods described in the link below. Or to answer your question, yes, Boot Repair CD will do the job just fine.

Useful link:

[https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader](https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader)

^^^
This.

---

### Post by Quarkrad on 2014-07-07
Boot Repair CD did it - many thanks.

---

