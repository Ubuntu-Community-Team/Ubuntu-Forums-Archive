---
title: "A Question about character encoding"
date: 2010-11-05
forum: Programming Talk
---

### Post by adit on 2010-11-05
I have a text file with 2 paragraphs.  Is it possible to encode the first paragraph in ISO 8859-7 and the second paragraph in Windows-1254 and save the file?
Does any character encoding apply to the entire file?

---

### Post by DanielWaterworth on 2010-11-05
sure it's possible, a file is just a blob of binary. I'm not sure that text editors would recognise it though. Why not just encode the whole thing in utf8?

---

