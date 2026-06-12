---
title: "HOWTO:Get Opera to work with CUPS"
date: 2005-12-25
forum: Outdated Tutorials &amp; Tips
---

### Post by desperado666 on 2005-12-25
Hi

If u wanna print with Opera and wonder why u cant print there is a solution i found.

Open terminal and write

cd /usr/lib
sudo ln -s libcups.so.2 libcups.so

Thats it!After Opera Restart u should be able to print to all your installed printers.

---

### Post by LordMau on 2006-04-19
Great tip, works for me!

---

### Post by LU7HQW on 2007-08-20
Hi!

This is my first post and new in linux.

I've been installed Xubuntu feisty, and i've been looking for a virtual printer, i made the installation of cups-pdf, but not works with opera, with Firefox and others programs works fine.

I try your solution with cups, but not works either.

Makes a file with the name _stdin_.pdf with 0 bytes in /home/username/PDF, and that's all.

Somebody could make work cups-pdf with opera?

I'm desperated, because i only use Opera...

Sorry my poor english, but this is a very good way to practice it.

---

### Post by slashdotfx on 2008-01-04
> **LU7HQW said:**
> Hi!

This is my first post and new in linux.

I've been installed Xubuntu feisty, and i've been looking for a virtual printer, i made the installation of cups-pdf, but not works with opera, with Firefox and others programs works fine.

I try your solution with cups, but not works either.

Makes a file with the name _stdin_.pdf with 0 bytes in /home/username/PDF, and that's all.

Somebody could make work cups-pdf with opera?

I'm desperated, because i only use Opera...

Sorry my poor english, but this is a very good way to practice it.

I'm experiencing this too, the only working solution at the moment is adding manual printer on Opera,

File-->Print, on tab "Printer Program", fill "Printer Program" with "lpr" and "Printer Parameter" with "-PVirtual_Printer" where "Virtual_Printer" is assumed to be your cups-pdf pseudo printer name.

I think we should fill a bug report to opera about this.

---

### Post by desperado666 on 2008-01-05
There are still problems with Opera 9.5 beta and cups-pdf.Whre to report opera spefic bugs?

---

