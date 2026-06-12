---
title: "[SOLVED] TarFile Python module help."
date: 2008-08-04
forum: Programming Talk
---

### Post by OutOfReach on 2008-08-04
I was looking over the Python library reference and found TarFile, It looked interesting so I decided to write a small practice script, everything works Ok, but I was wondering if it is possible to exclude certain files/directories from being archived. Something like this in bash form:

```
tar cvpjf zippedfiles.tar.bz2 --exclude=/home/pwnz/Documents/Other --exclude=/home/pwnz/Desktop/textfile.txt --exclude=/home/pwnz/zippedfiles.tar.bz2 /home/pwnz/
```

---

### Post by xelapond on 2008-08-04
I have never looked at TarFile myself, but you could always do this:

[PHP]import os
tar_command = '
tar cvpjf zippedfiles.tar.bz2 --exclude=/home/pwnz/Documents/Other --exclude=/home/pwnz/Desktop/textfile.txt --exclude=/home/pwnz/zippedfiles.tar.bz2 /home/pwnz/'

os.system(tar_command)
[/PHP]

os.system lets you call a bash command.  I don't know if that is what you are looking for, but it should work as a temporary hack.

---

### Post by OutOfReach on 2008-08-04
That's what I was thinking about doing, I was reading up and found that in Python 2.6, Python will support an exclude argument, so in until Python 2.6 is released I'll just have to find a workaround.

---

### Post by ghostdog74 on 2008-08-04
Why would you want to call system tar when the tarfile module is there for you to use ? Practice writing portable code whenever possible. If you look at the [docs](http://docs.python.org/lib/tar-examples.html) examples on tarfile, you will see you need to use add() to create an archive. So just simple go through the directory, looking for files you want to exclude. eg
```

for files in os.listdir(path):
   if files[-3:] not in ["txt","jpg"];
       # create tar 

```

---

### Post by OutOfReach on 2008-08-04
Thanks for the reply, I tried this:
```
>>> for files in os.listdir("/home/pwnz/Desktop/Scripts"):
...     if files[-3:] not in ["txt"]:
...         tar = tarfile.open("ScriptsFile.tar.bz2", "w:bz2")
...         tar.add(files)
...         tar.close()
... 

```

but it gave me this:

```
Traceback (most recent call last):
  File "<stdin>", line 4, in <module>
  File "/usr/lib/python2.5/tarfile.py", line 1460, in add
    tarinfo = self.gettarinfo(name, arcname)
  File "/usr/lib/python2.5/tarfile.py", line 1333, in gettarinfo
    statres = os.lstat(name)
OSError: [Errno 2] No such file or directory: 'leapyear.py'
```

But indeed there is a file name 'leapyear.py'.
Any ideas?

---

### Post by ghostdog74 on 2008-08-04
troubleshoot your script step by step. Remove all the tar commands, just print the files. post here. Also, put your python commands in a script.

---

### Post by OutOfReach on 2008-08-04
Ok, the new script:

```
#!/usr/bin/env python

import os

for files in os.listdir("/home/pwnz/Desktop/Scripts"):
    if files[-3:] not in ["txt"]:
        print files,
```

Which outputs:
```
leapyear.py NumberGenerator.py 99Bottles.py NumberGenerator.py integer.py valid.py charcount.py

```

And no errors.

It looks like it works, since it didn't output the .txt files that were in there.
So I'm guessing that the problem is with the TarFile module?

---

### Post by ghostdog74 on 2008-08-04
try putting tar.close() outside the for loop, so that it closes after every file is added. Also, put our tar.open() outside the for loop. You don't need to open it everytime a file is found.

---

### Post by OutOfReach on 2008-08-04
Modified script:

```
#!/usr/bin/env python

import os
import tarfile

tar = tarfile.open("ScriptsFile.tar.bz2", "w:bz2")

for files in os.listdir("/home/pwnz/Desktop/Scripts"):
    if files[-3:] not in ["txt"]:
        tar.add(files)
        
tar.close()
```

Which gives the same error:
```
Traceback (most recent call last):
  File "exclude.py", line 10, in <module>
    tar.add(files)
  File "/usr/lib/python2.5/tarfile.py", line 1460, in add
    tarinfo = self.gettarinfo(name, arcname)
  File "/usr/lib/python2.5/tarfile.py", line 1333, in gettarinfo
    statres = os.lstat(name)
OSError: [Errno 2] No such file or directory: 'leapyear.py'

```

---

### Post by ghostdog74 on 2008-08-04
it works fine for me in python 2.4. You can put tar.debug=3 to see what other messages you have.

---

### Post by OutOfReach on 2008-08-04
Interesting, that it works for you in python 2.4.
I added tar.debug=3 and all it did was output 'leapyear.py' before the usual error.

---

### Post by ghostdog74 on 2008-08-04
last try, remove all other directories under the current directory, remove leapyear.py. Run it again and see what happens.

---

### Post by OutOfReach on 2008-08-04
Ok I moved leapyear.py, but now it says NumberGenerator.py doesn't exist, which, interestingly comes first when I print os.listdir("/home/pwnz/Desktop/Scripts").

---

### Post by ghostdog74 on 2008-08-04
change dir to /home/pwnz/Desktop/Scripts first
eg
```


os.chdir("/home/pwnz/Desktop/Scripts")
for file in os.listdir(....)
...

..
```

---

### Post by OutOfReach on 2008-08-04
That actually worked!!
Now I have a nice .tar.bz2 with .py files! :)
Thank you! Not only for helping me but for being patient, lol.
Thanks!

---

