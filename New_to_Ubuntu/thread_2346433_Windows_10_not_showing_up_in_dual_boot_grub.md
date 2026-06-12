---
title: "Windows 10 not showing up in dual boot grub"
date: 2016-12-14
forum: New to Ubuntu
---

### Post by alfrdpennyworth on 2016-12-14
I'm selling my pc, and I wiped the hard drive using window 10's "reset" feature and did a secure wipe. I left it do its thing, and when I booted the computer up it only had ubuntu available. I'be already tried boot-repair.

---

### Post by QIII on 2016-12-14
Hello!

In what way does this not match your expectations?

---

### Post by alfrdpennyworth on 2016-12-14
I hadn't known that it would delete my windows 10. Or at least remove the option from the grub.

---

### Post by QIII on 2016-12-14
You said you did a secure wipe.  Did you wipe your Win 10 partition after you "reset" it?

---

### Post by alfrdpennyworth on 2016-12-14
Not that I know of. I let windows do its whole reset thing, and when I turned on the computer, the windows 10 option was gone

---

### Post by oldfred on 2016-12-14
UEFI or BIOS.

Best to always reset system to Windows boots before deleting Ubuntu partition. Most of grub is in Ubuntu partition including boot menu.

Usually the system reset assumes BIOS or UEFI settings are fine. So they are not reset.

If BIOS you must reinstall a Windows type boot loader and make sure Windows boot partition, usually the 100MB one has boot flag.
If UEFI, just go into UEFI and reset to make Windows default boot.

       How to restore the Ubuntu/XP/Vista/7/8/10 BIOS bootloader 
[https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader](https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader)

---

