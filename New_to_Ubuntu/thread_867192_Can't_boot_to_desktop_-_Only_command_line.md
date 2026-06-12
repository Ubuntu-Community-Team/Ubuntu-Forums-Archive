---
title: "Can't boot to desktop - Only command line"
date: 2008-07-22
forum: New to Ubuntu
---

### Post by mr.moch on 2008-07-22
I installed Ubuntu via Wubi, which was contained in the Ubuntu 8.04 ISO.  However, when I booted into Ubuntu, it sent me to a command line "BusyBox".  When I tried using the Safe Installer using <can't remember name>, there was an error stating "I/O error on fd0, sector 0".  There was no floppy disk in the drive anyways.  How can I get it to boot into the desktop????

---

### Post by halitech on 2008-07-22
when you did the install, did you install grub to a floppy?

> I/O error on fd0, sector 0

seems to be indicating that it is looking for a floppy for some reason

---

### Post by Separ on 2008-07-22
I had a problem when I first used ubuntu which was like this and it may be something to do with the drivers that the Live CD has.

You could try adding these two things to the boot options:
```
acpi=off maxcpus=0
```
And see if that works.

---

### Post by mr.moch on 2008-07-22
halitech:  GRUB was installed to the HDD via Wubi, as stated earlier.
Separ:  > **Separ said:**
> You could try adding these two things to the boot options:
```
acpi=off maxcpus=0
```
           I'll try it and come back w/a response.

---

### Post by mr.moch on 2008-07-22
i cant seem to find where to put it. if you mean the grub menu, then it didnt work.

---

### Post by mr.moch on 2008-07-22
***bump***

---

### Post by mr.moch on 2008-07-22
Anybody?????????????????????????????????????????  Please?

---

### Post by Separ on 2008-07-22
sorry, on grub boot press 'e' twice to edit the line and add them and press 'b' to boot.

---

### Post by mr.moch on 2008-07-22
FYI, it didn't work.  It would skip the floppy disk, but it would still go to BusyBox.

---

