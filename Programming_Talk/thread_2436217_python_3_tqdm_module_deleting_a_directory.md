---
title: "python 3 tqdm module deleting a directory"
date: 2020-02-02
forum: Programming Talk
---

### Post by lance bermudez on 2020-02-02
Want a progress bar for deleting a directory

errror i get is
```

/home/lance/plex/powershell
Python Version:  3.7.5 (default, Nov 20 2019, 09:21:52) 
[GCC 9.2.1 20191008]
OS Platform:  linux
/home/lance/Documents
Removing Old Files

  0%|          | 0/100 [00:00<?, ?it/s]
  0%|          | 0/100 [00:00<?, ?it/s]
Traceback (most recent call last):
  File "/home/lance/plex/powershell/PythonCopyFiles.py", line 30, in <module>
    rmtree('/home/lance/Documents/Music')
  File "/usr/lib/python3.7/shutil.py", line 485, in rmtree
    onerror(os.lstat, path, sys.exc_info())
  File "/usr/lib/python3.7/shutil.py", line 483, in rmtree
    orig_st = os.lstat(path)
FileNotFoundError: [Errno 2] No such file or directory: '/home/lance/Documents/Music'

```

my python code is
```

from os import chdir         # os.chdir
from os import getcwd        # os.getcwd
from os import getenv        # os.getenv
from os.path import isdir    # os.path.isdir
from shutil import rmtree    # shutil.rmtree
from sys import version
from sys import platform
from tqdm import tqdm
print(getcwd())
print('Python Version: ', version)
print('OS Platform: ', platform)
if platform == 'linux':
    chdir(join(getenv('HOME'), 'Documents'))
    print(getcwd())
    if isdir('/home/lance/Documents/Music'):
        print('Removing Old Files')
        for i in tqdm(range(0,100)):
            rmtree('/home/lance/Documents/Music')

```

---

### Post by spjackson on 2020-02-03
The reason you are getting the error is this. Your for loop says to call rmtree 100 times with the same path. Once the first iteration of the loop completes successfully, the directory no longer exists. Therefore rmtree will fail during the second iteration of the loop.

As far as I can see, shutil.rmtree doesn't provide any hooks for you to determine how many "steps" there are (e.g. count of files/directories) and to execute step N.

---

