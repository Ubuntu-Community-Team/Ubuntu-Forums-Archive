---
title: "identical file searching"
date: 2010-02-07
forum: Programming Talk
---

### Post by studybuddy09 on 2010-02-07
How do i search to check if two files have the same content or not??In other words,to find two identical files in a directory tree.Is it possible to pipe the output of every file into another file and match it??
Please help me..

---

### Post by Kegusa on 2010-02-07
To see if two files are identical in contents you can use md5sum and a quick bash script to compare the md5sums. The following is just a brief description of md5sum (this package is default in ubuntu)

```

Create 3 different directories for the test
mkdir /tmp/test1 /tmp/test2 /tmp/test3

Now create 3 files, 2 with same name and 1 foo file in the directories:
touch /tmp/test1/file /tmp/test2/file /tmp/test3/foo

now compare the 3 different files in each directory with md5sum:

md5sum /tmp/test1/file /tmp/test2/file /tmp/test3/foo
```

Someone a bit more proficient in bash scripting might help you out with making a script like this or if you know it yourself go ahead and make it! 

Best of luck.

---

### Post by lavinog on 2010-02-07
here is a python script that can generate a list of files with matching md5s:
```

#!/usr/bin/env python

import os
import hashlib
import sys
SHOWSTATUS = True
MAXFILESIZE = 100  #Mb
SKIPEMPTY = True

def get_md5(file):

    m = hashlib.md5()
    f = open(file, 'rb') # open in binary mode
    while True:
        buffer = f.read(1024)
        if len(buffer) == 0: break # end of file
        m.update(buffer)
    return m.hexdigest()
  

def finddupes(rootpath='.'):
    md5dict={}
    for dirpath, dirnames, filenames in os.walk( rootpath ):
        
        for file in filenames:
            f = os.path.join(dirpath,file)
                
            try:
                fsize = os.stat(f).st_size
            except:
                continue
            
            
            if SKIPEMPTY and fsize == 0:
                continue
    
            if fsize / 1024000 > MAXFILESIZE: continue
            
            
            m=get_md5(f)
            
            if m in md5dict.keys():
                md5dict[m].append(f)
                if SHOWSTATUS: 
                    sys.stdout.write('X')
                    sys.stdout.flush()

            else:
                if SHOWSTATUS: sys.stdout.write('.')
                sys.stdout.flush()
                md5dict[m]=[f]
    
    return md5dict


def outputdupes(md5dict):
    for md5,files in md5dict.items():
        if len(files)>1:
            print '='*20
            for file in files:
                print file

def main():
    if len(sys.argv)>1:
        rootpath = sys.argv[1]
    else:
        rootpath = '.'
    
    md5dict = finddupes( rootpath )
    outputdupes(md5dict)


if __name__ == '__main__': main()

```

save it to a file named finddupes.py
execute it with:
```

python finddupes.py folder

```
where folder is the starting folder you want to check.

---

