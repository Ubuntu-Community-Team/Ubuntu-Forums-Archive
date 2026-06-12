---
title: "Struggling with encoding of txt files"
date: 2007-05-20
forum: Programming Talk
---

### Post by HeavyEddie on 2007-05-20
I'm writing several php apps and distributing them.  They were originally written on a windows system, but now that I'm using Ubuntu and bluefish folks have to upload the files in binary for them to work?  

Bluefish is using UTF-8.  I simply need this to work with as little fuss to the folks uploading the scrips as possible.  Any insight or advise?

---

### Post by HeavyEddie on 2007-05-20
So, took a hex editor and compared the same two files.  One save on Windows as ANSI and the other saved using Kate.  The one character that I can visibly see as incorrect appears as a dash in windows but a box (place holder) in linux. 

On windows that character is saved as hex 2D but on the linux box it is hex 96.

After saved by the Windows computer it will then display appropriately in kate as well.

So, I guess the big question is what would have converted a hex 2D to a hex 96?  Could it have been when I was zipping up the files?

---

