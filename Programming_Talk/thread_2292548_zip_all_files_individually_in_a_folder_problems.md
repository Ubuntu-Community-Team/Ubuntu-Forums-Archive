---
title: "zip all files individually in a folder problems"
date: 2015-08-29
forum: Programming Talk
---

### Post by lance bermudez on 2015-08-29
Python 3.4 script that will individually zip all files in a dir folder
```

import shutil
import os
import zipfile

def csv_files(source_dir):
    for filename in os.listdir(source_dir):
         yield filename

source_dir = '/tmp/tester'  # r'C:\users\xyz\Source\'
dest_dir = '/tmp/tester/test'   # r'C:\users\xyz\Dest\'

os.chdir(dest_dir)  # To work around zipfile limitations

for csv_filename in csv_files(source_dir):
    file_root = os.path.splitext(csv_filename)[0]
    zip_file_name = file_root + '.zip'
    zip_file_path = os.path.join(dest_dir, zip_file_name)
    with zipfile.ZipFile(zip_file_path, mode='w') as zf:
        zf.write(csv_filename)

```

error I'm getting
```

>>> ================================ RESTART ================================
>>> 
Traceback (most recent call last):
  File "/home/lance/bin/python/zip_files_in_dir.py", line 21, in <module>
    zf.write(csv_filename)
  File "/usr/lib/python3.4/zipfile.py", line 1326, in write
    st = os.stat(filename)
FileNotFoundError: [Errno 2] No such file or directory: 'dice.py'

```

---

### Post by spjackson on 2015-08-29
The reason it is failing is that you give the name of the source file without any path and the file does not exist in the current directory (dest_dir).

Instead of this
> 
```

os.chdir(dest_dir)  # To work around zipfile limitations

```

do this
```

os.chdir(source_dir)  # To work around zipfile limitations

```

---

