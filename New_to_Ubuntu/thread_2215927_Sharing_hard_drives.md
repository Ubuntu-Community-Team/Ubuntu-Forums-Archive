---
title: "Sharing hard drives"
date: 2014-04-09
forum: New to Ubuntu
---

### Post by Gelman on 2014-04-09
I am considering installing Ubuntu 12.04 LTS 32 bit along side Windows XP on my PC. If I had an external hard drive for documents, music and photographs would I be able to access them from Umbutu as well as Windows? In other words use an external hard drive as a shared source?

---

### Post by sudodus on 2014-04-09
Welcome to the Ubuntu Forums :-)

Yes, the file system of Windows, NTFS, can be read by Ubuntu. It is OK to keep Windows XP, but avoid using it with the internet now that it has passed end of life. I suggest that you copy whatever personal files there are to a linux partition and prepare for shutting down XP.

But the reverse does not work. Windows cannot read the standard ext4 file system of Ubuntu.

-o-

Please specify your computer, and it will be possible to give detailed tips about what version and flavour to install!

- Brand name and model
- CPU
- RAM (size)
- graphics chip/card
- wifi chip/card

And before you decide to install Ubuntu (or some community flavour of it), try some versions/flavours 'live' booted from a CD/DVD/USB drive.

---

### Post by TheFu on 2014-04-09
Only if the file system used is NTFS - but that will not honor any permissions. Basically it is readable by anyone. That is usually fine at home, for data files.

So - yes.

---

