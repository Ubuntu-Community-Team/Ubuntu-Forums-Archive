---
title: "Find all png files and copy the to other directory Unix Shell Scripting"
date: 2010-05-08
forum: Programming Talk
---

### Post by hakermania on 2010-05-08
I want to find all png files in a directory and copy them to other.. it should be something like
cp `find *.png` /home/$USER/Desktop/images
but the directory in which I want to find the pngs has other subfolders. For example i am in the /home/alex/Desktop/PNGFILES and in this folder there are the folders nicePNGS gardernPNGS etc etc
So I want to search all these folders for PNG files and copy them to an other directory....Any help?

---

### Post by Seal Daemon on 2010-05-08
```
find /base/dir -name *.png -exec cp {} /destination/dir \;

```

Is this what you were looking for ?

---

### Post by hakermania on 2010-05-08
yeah, ok thank you very much

---

