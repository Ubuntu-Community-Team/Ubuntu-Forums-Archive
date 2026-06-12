---
title: "An equivalent to mbtPdfAsm"
date: 2007-03-21
forum: Programming Talk
---

### Post by dawguk on 2007-03-21
Hi all,

I'm currently looking for a shell application that will read the number of pages that a PDF file has in it, and just throw a number back to the terminal. I'm currently using mbtPdfAsm, but it fails with long path names, and various other things (like reading certain PDFs).

I would even consider writing my own script, if I could find out more information about PDF file headers, and the such.

Can anyone help me out at all? Many thanks in advance.

---

### Post by tomchuk on 2007-03-21
Install pdftk from universe and use:
```
pdftk <filename> dump_data | grep NumberOfPages | awk '{print $2}'
```

---

