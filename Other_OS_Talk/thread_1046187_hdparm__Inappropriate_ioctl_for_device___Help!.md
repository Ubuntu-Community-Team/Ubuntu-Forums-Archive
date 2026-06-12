---
title: "hdparm:  Inappropriate ioctl for device  ??? Help!"
date: 2009-01-21
forum: Other OS Talk
---

### Post by mips on 2009-01-21
I have a HP nx6110 laptop with Seagate ST94011A 40GB PATA HD. The HD performance is less than great and and sudo hdparm -i /dev/sda confirms not all settings are optimal.

Whenever I try to issue a command I get returned **XXXX failed: Inappropriate ioctl for device** despite the fact that it should be supported on the drive.

Can anyone enlighten me as to what is going on, does hdparm even still work?

Btw, I'm using Arch 2.6.28 but this is not really the issue.

Googling has not helped much as I see a lot of the same quistion but no answers...

Edit: bit more browsing reveals this might have something to do with "libata", but what? Looks like more reading...

---

### Post by mips on 2009-01-21
Hmm, think I found the answers at [http://linux-ata.org/faq.html](http://linux-ata.org/faq.html)

Lookes like I'm fooked for now and will have to run in 16-bit mode as well as just accept not being able to tweak things.

For all intense purposes hdparm has become obsolete if you ask me.

If anyone has any ideas or workarounds please feel free to share as this stuff is a bit greek to me.

---

