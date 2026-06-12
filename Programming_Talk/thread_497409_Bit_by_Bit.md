---
title: "Bit by Bit"
date: 2007-07-10
forum: Programming Talk
---

### Post by raddellee on 2007-07-10
Hello i was wondering what the code is (if any) to make a copy of a cd/dvd in iso format  bit by bit only, help will be appreciated.

---

### Post by anthro398 on 2007-07-10
dd if=/dev/cdrom bs=2048 count=326239 conv=notrunc,noerror > file-name.iso

See 'man dd' for more information on what those parameters do.

---

