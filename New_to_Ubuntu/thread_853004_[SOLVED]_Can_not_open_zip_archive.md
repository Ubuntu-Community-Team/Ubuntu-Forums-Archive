---
title: "[SOLVED] Can not open zip archive"
date: 2008-07-08
forum: New to Ubuntu
---

### Post by daniel7860 on 2008-07-08
i have a 7.8 GB big   .zip archive and when i try to open it with archive manager it says: An error occurred while loading the archive.
command line output: 




Archive:  /home/daniel/Downloads/archive.zip   -251608659   271
warning [/home/daniel/Downloads/archive.zip]:  -251663984 extra bytes at beginning or within zipfile
  (attempting to process anyway)
error [/home/daniel/Downloads/archive.zip]:  start of central directory not found;
  zipfile corrupt.
  (please check that you have transferred or created the zipfile in the
  appropriate BINARY mode and that you have compiled UnZip properly)

1 archive had fatal errors.


can anybody help:confused:    this took weeks to download and now i am so disappointed:(

---

### Post by Polygon on 2008-07-08
the zipfile might be corrupted, do you know anyone else who successfully downloaded the file?

---

### Post by daniel7860 on 2008-07-08
i solved it,,,    
had to copy it to my windows partition and extract it there using winzip.
then copy it back to my Ubuntu partition.

---

### Post by TenPlus1 on 2008-07-08
Sometimes I have trouble with the odd .zip file too, but I use Xarchiver and that seems to unpack it no problem...

---

