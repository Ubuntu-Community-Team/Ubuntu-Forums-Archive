---
title: "How to print .odt files from command line ?"
date: 2023-11-26
forum: New to Ubuntu
---

### Post by oden99 on 2023-11-26
I try using the lpr command to print .odt files from command line, but I get
"lpr: Unsupported document-format "application/vnd.oasis.opendocument.text"."

.txt files work as expected.
I set the PRINTER env variable to my printers registered name.

$ echo $PRINTER
Brother_HL_L2350DW_series

Printing from gui works with .odt files and from Open office and most other software with printing option.

Is there something I need to install to print.odt from the command line ?

Ubuntu 22.04

---

### Post by ActionParsnip on 2023-11-26
```

lowriter -p filename.odt

```

---

