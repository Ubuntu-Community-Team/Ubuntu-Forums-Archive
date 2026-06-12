---
title: "[SOLVED] Image Magick: Passing on old filenames to converted version."
date: 2008-11-27
forum: New to Ubuntu
---

### Post by Slime mold on 2008-11-27
I am converting many of my photo at once, but when I tested this program, it renames them all to *-NUMBERHERE.PNG

Is there a way to make the new photo inherit the name of the old one automatically?

---

### Post by kpkeerthi on 2008-11-27
This should get you started. 
```

#!/bin/bash
for file in *.png
do
   new_name_prefix=$(basename $(file))
   echo $new_name_prefix
   convert $file ${new_name_prefix}.jpg
done

```

Save the content to a file convert.sh and then ```
chmod +x convert.sh
```
To run the script:
```
./convert
```

---

### Post by vanadium on 2008-11-27
The "mogrify" command will overwrite the original file, while "convert" will create a new file. Be sure to use mogrify only if you have a backup of your files.

---

### Post by Slime mold on 2008-11-27
> **kpkeerthi said:**
> This should get you started. 
```

#!/bin/bash
for file in *.png
do
   new_name_prefix=$(basename $(file))
   echo $new_name_prefix
   convert $file ${new_name_prefix}.jpg
done

```

Save the content to a file convert.sh and then ```
chmod +x convert.sh
```
To run the script:
```
./convert
```
Thank you!

> **vanadium said:**
> The "mogrify" command will overwrite the original file, while "convert" will create a new file. Be sure to use mogrify only if you have a backup of your files.

I have har dopy-type backup, so it is good, THANK YOU!

---

