---
title: "(python) mime-type"
date: 2006-04-03
forum: Programming Talk
---

### Post by dabear on 2006-04-03
Hi, I want to find out weather or not a file really is an iso file. How do I do that?
Checking the extension isn't hard, but I really would like to check if the contents of a file is what the file extension claims. Any idea?

---

### Post by pranith on 2006-04-03
hi,
       there is a command calles [COLOR="DarkRed"]file[/COLOR] in unix that does the job for u.... It tells the type of the file by probing some of the contents.
all u need to do is 
import os
os.system("file "+$filename)

hope that helps
pranith.

---

