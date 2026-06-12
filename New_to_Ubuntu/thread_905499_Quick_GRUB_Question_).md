---
title: "Quick GRUB Question :)"
date: 2008-08-30
forum: New to Ubuntu
---

### Post by zamadatix on 2008-08-30
will grub allow me to boot of a usb stick even if my laptop bios doesnt?

---

### Post by gmxgeek on 2008-08-30
No. If your BIOS doesn't support usb boot, then your hardware can't handle it, and it is not possible.

---

### Post by zamadatix on 2008-08-30
i thought i heard of programs allowing a usb boot on a bios that doesnt support it.

---

### Post by gmxgeek on 2008-08-30
to my knowlege no, but i could be mistaken.

---

### Post by MasterSander on 2008-08-30
> **zamadatix said:**
> i thought i heard of programs allowing a usb boot on a bios that doesnt support it.

No, it's as gmxgeek says, if your BIOS doesn't support USB boot, then you can't boot on a USB, you can try updating your bios though, perhaps in some newer versions of your bios, it is enabled, unless ofcourse your hardware doesn't support it at all.

---

### Post by lswb on 2008-08-30
You can't boot directly from USB if your BIOS doesn't support it. But, you can install grub on a hard drive that has a small partition with a kernel and enough drivers to recognize the USB drive. Use grub to boot the small partition, then finish booting with the files on USB. I've seen the procedure described on various websites and forums but have not tried it myself, you'll have to do some googling to find a procedure that works for your system.

---

