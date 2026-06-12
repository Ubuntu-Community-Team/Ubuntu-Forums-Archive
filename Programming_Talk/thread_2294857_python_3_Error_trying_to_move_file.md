---
title: "python 3 Error trying to move file"
date: 2015-09-14
forum: Programming Talk
---

### Post by lance bermudez on 2015-09-14
I'm trying to move a zip file to a directory then unzip the file keeping the file name it has but with out the zip. So far  I can not do it keep getting this error

error is
```

Traceback (most recent call last):
  File "/usr/lib/python3.4/shutil.py", line 523, in move
    os.rename(src, real_dst)
FileNotFoundError: [Errno 2] No such file or directory: 'docs-0.97.zip' -> '/home/lance/iso/Data_Files/docs-0.97.zip'

During handling of the above exception, another exception occurred:

Traceback (most recent call last):
  File "/home/lance/iso/test.py", line 8, in <module>
    shutil.move(files,destination)
  File "/usr/lib/python3.4/shutil.py", line 535, in move
    copy2(src, real_dst)
  File "/usr/lib/python3.4/shutil.py", line 245, in copy2
    copyfile(src, dst, follow_symlinks=follow_symlinks)
  File "/usr/lib/python3.4/shutil.py", line 108, in copyfile
    with open(src, 'rb') as fsrc:
FileNotFoundError: [Errno 2] No such file or directory: 'docs-0.97.zip'

```

code for script
```

import shutil, os, zipfile

source = os.listdir(os.path.join(os.getenv('HOME'),'Downloads')) # move file from
destination = (os.path.join(os.getenv('HOME'),'iso/Data_Files')) # fle move to

for files in source:
    if files.endswith('.zip'):
        shutil.move(files,destination)

```

---

### Post by spjackson on 2015-09-14
os.listdir returns only the filenames, not their path, so when you come to move the file, you need to supply the path as well as the name. e.g.
```

import shutil, os, zipfile

sourcedir = os.path.join(os.getenv('HOME'),'Downloads')
source = os.listdir(sourcedir)
destination = (os.path.join(os.getenv('HOME'),'iso/Data_Files')) # fle move to

for files in source:
    if files.endswith('.zip'):
        shutil.move(os.path.join(sourcedir,files),destination)

```

---

