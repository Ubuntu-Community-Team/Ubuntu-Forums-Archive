---
title: "How to burn two Iso files on same disk"
date: 2008-09-27
forum: New to Ubuntu
---

### Post by Foxfire on 2008-09-27
I have a dual layer disk and 2 iso files 3gb a piece I want them on the same disk how do i do this

---

### Post by Xiong Chiamiov on 2008-09-27
afaik, you can't

I'm assuming you're talking about Linux isos, not movies or somesuch, which you would need to combine into one iso.

---

### Post by bumanie on 2008-09-27
isomaster may help - it allows adding, deleting of files to/from .iso's> sudo apt-get install isomasterThe other possibility is to do a normal 'cp' command to join two files into one - have backups of your iso's just in case it doesn't work as planned > cp file1.iso file2.iso newfile.isowhere file1 is the first iso, file2 is the second iso and the destination file, with the two joined is newfile.iso Not sure how that wil work with .iso's but it is how it is done with 'regular' files.

---

### Post by kansasnoob on 2008-09-27
Why?

---

