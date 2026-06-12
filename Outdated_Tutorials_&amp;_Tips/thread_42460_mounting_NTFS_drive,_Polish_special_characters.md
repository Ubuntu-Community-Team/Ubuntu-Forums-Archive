---
title: "mounting NTFS drive, Polish special characters"
date: 2005-06-17
forum: Outdated Tutorials &amp; Tips
---

### Post by chopeen on 2005-06-17
I have moved to Ubuntu (system language: English - for me computers speak in English) from Windows XP (system language: Polish - for Windows vendors in Poland this OS speaks only in Polish).

I had no problem to mount Windows NTFS partition. However, most of the Polish characters were not displayed correctly.

It took me some time, but I have finally worked out what options to use - this is what I do to mount a Windows partition in read-only mode:

sudo mount -t ntfs -o umask=0222,nls=utf8 /dev/hdb4 /mnt/windows

However, remember that not all file browsers will display correct characters.
- Nautilus can handle all Polish letters.
- Krusader handles all of them but one properly.
- Midnight Commander (mc) cannot display them.

---

