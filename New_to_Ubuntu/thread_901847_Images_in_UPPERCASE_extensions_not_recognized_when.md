---
title: "Images in UPPERCASE extensions not recognized when uploading images in Firefox"
date: 2008-08-26
forum: New to Ubuntu
---

### Post by TRANQU111TY on 2008-08-26
On a usual online social site in most cases I need to rename my .JPG images to lowercase .jpg otherwise I can't see the images I want to upload. Can I get a fix?

---

### Post by eightmillion on 2008-08-26
I don't know the source of the problem, but you can use a bash script to batch rename the files.
```

#!/usr/bin/env bash

for FN in *.JPG
do
mv "${FN}" "${FN/.JPG/.jpg}"
done


```
Just save this as jpgfixer and make it executable with: **chmod +x jpgfixer**
Drop it in the directory with the problem files and run it with: **./jpgfixer**

---

