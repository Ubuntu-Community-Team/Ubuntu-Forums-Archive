---
title: "info printf"
date: 2006-05-29
forum: Programming Talk
---

### Post by rplantz on 2006-05-29
"info printf" brings up the manpage. I cannot find the package I need to install in order to get info for printf.

info works for other things, e.g., gcc, make, so it seems to be properly installed.

---

### Post by toojays on 2006-05-30
The printf info documentation is in the C library manual. Install the glibc-doc package, then you can get to the section on printf with "info libc --index-search printf". Actually, "info libc" followed by typing iprintf<cr> is a quicker way to get there. :)

---

### Post by rplantz on 2006-05-31
[QUOTE=toojays]The printf info documentation is in the C library manual. Install the glibc-doc package, then you can get to the section on printf with "info libc --index-search printf". Actually, "info libc" followed by typing iprintf<cr> is a quicker way to get there. :)[/QUOTE]

Thank you. I already had it installed -- just didn't know how to get there. I think I've done this before, in the distant past.

---

