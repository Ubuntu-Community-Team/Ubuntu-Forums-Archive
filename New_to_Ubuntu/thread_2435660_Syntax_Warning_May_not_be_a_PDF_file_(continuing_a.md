---
title: "Syntax Warning: May not be a PDF file (continuing anyway)"
date: 2020-01-23
forum: New to Ubuntu
---

### Post by kelvinho2 on 2020-01-23
Hi,

I have this issue on my Ubuntu desktop 18.04.
When I execute pdfinfo on a valid pdf file, I get the following result:

==========================================
Syntax Warning: May not be a PDF file (continuing anyway)
Syntax Error (2): Illegal character <68> in hex string
Syntax Error (3): Illegal character <74> in hex string
Syntax Error (4): Illegal character <6d> in hex string
Syntax Error (5): Illegal character <6c> in hex string
Syntax Error (10): Illegal character <68> in hex string
Syntax Error (16): Illegal character <74> in hex string
Syntax Error (17): Illegal character <69> in hex string
Syntax Error (18): Illegal character <74> in hex string
Syntax Error (19): Illegal character <6c> in hex string
Syntax Error: Couldn't find trailer dictionary
Syntax Error: Couldn't find trailer dictionary
Syntax Error: Couldn't read xref table
==========================================

However, when I run it on Ubuntu server 18.04, the following result appears:
==========================================
Title:          
Subject:        
Keywords:       
Author:         SeaStarNet
Creator:        WHMCS
Producer:       TCPDF 6.2.12 ([http://www.tcpdf.org](http://www.tcpdf.org))
CreationDate:   Wed Apr 18 17:42:20 2018 WIB
ModDate:        Wed Apr 18 17:43:14 2018 WIB
Tagged:         no
UserProperties: no
Suspects:       no
Form:           none
JavaScript:     no
Pages:          1
Encrypted:      no
Page size:      595.276 x 841.89 pts (A4)
Page rot:       0
File size:      16380 bytes
Optimized:      no
PDF version:    1.7
==========================================

The error message from above prevents me from performing actions to the file. 
I understand that this could be due to the file being amended by a pdf writer.
However, such a situation cannot be avoided as it is part of our operations.
Thus, could there be a solution to my situation?

Thanks!

---

### Post by wildmanne39 on 2020-01-23
*Thread moved to **New to Ubuntu a more appropriate sub-forum**.*

---

### Post by Impavidus on 2020-01-24
Is the file identical? Test by calculating a hash on each computer:```
md5sum file.pdf
```Maybe the file got corrupted during transfer to your desktop. It's either that or you somehow got a broken pdfinfo on that desktop.

---

### Post by kelvinho2 on 2020-01-27
3770d6c02352ab136db0d9449e9e85a1
3770d6c02352ab136db0d9449e9e85a1

They are identical. The files are not corrupted as I can read them using a pdf viewer. 
Actually, the original file is on the desktop and is copied to the server.

I understand from my research is that this is due to the level of strictness Linux deals with pdf files. 
This issue was resolved, however, seems that I am still experiencing it on the desktop version.

---

### Post by Impavidus on 2020-01-28
If the files are identical and pdfinfo gives different output on desktop and server, pdfinfo must be different (or, more worrying, you get random bitflips). As both run Ubuntu 18.04 and therefore use the same repositories, that shouldn't happen. Can you show the output of```
pdfinfo -v
apt-cache policy poppler-utils
```on both computers?

---

