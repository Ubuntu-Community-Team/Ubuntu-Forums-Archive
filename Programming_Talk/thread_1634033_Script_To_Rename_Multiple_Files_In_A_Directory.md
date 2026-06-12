---
title: "Script To Rename Multiple Files In A Directory"
date: 2010-11-30
forum: Programming Talk
---

### Post by jsmidt on 2010-11-30
Hey, I don't know if this is the best forum but here it goes:

I have a directory with many files called:

ch1_ch12_001.txt
ch1_ch12_002.txt
ch1_ch12_003.txt
etc...

I want to change the names of these files to:

ch1_001.txt
ch1_002.txt
ch1_003.txt
etc...

removing the first _ch12 from each filename.  Does anyone know a script that can do this?  Thanks.

---

### Post by endotherm on 2010-11-30
not a script per se, but you may want to try pyrenamer (in the repos). or if you want, write up a quick .py. use os.walk to iterate over the files, and use string.replace on each filename, replacing the chapter token with "". then use shutil.move to rename the file.

---

### Post by mo.reina on 2010-11-30
in python:

```
import glob
import os

filelist = glob.glob('*')
for f in filelist:
  newname = f[:3] + f[8:]
  os.rename(f, newname)
```

make sure that the only files in the directory are those that you want to change and that the format is as stated above, ch1_xxxx_xxx.txt, otherwise the code will fail.

---

### Post by mobilediesel on 2010-11-30
> **jsmidt said:**
> Hey, I don't know if this is the best forum but here it goes:

I have a directory with many files called:

ch1_ch12_001.txt
ch1_ch12_002.txt
ch1_ch12_003.txt
etc...

I want to change the names of these files to:

ch1_001.txt
ch1_002.txt
ch1_003.txt
etc...

removing the first _ch12 from each filename.  Does anyone know a script that can do this?  Thanks.

The perl **rename** script is available on most Debian/Ubuntu based distros.
```
rename 's/_ch12//' *.txt
```

---

### Post by jsmidt on 2010-11-30
Thank you all.  Those scripts worked!

---

