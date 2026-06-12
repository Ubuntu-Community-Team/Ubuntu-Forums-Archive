---
title: "Python on Windows"
date: 2015-02-14
forum: Programming Talk
---

### Post by lance bermudez on 2015-02-14
I know that ubuntu is linux but the form said any programing questions so I have python 3 on windows and I cant seem to get it to copy a dir with the files in side to another dir

#copy files and folders of Dir
import os
file="C:\User\lance\Documents\*.txt"
dfile="C:\Users\lance\Documentss\Documents"
os.system('copy "file" "dfile"')


C:\Users\lance\Downloads>python test.py
  File "test.py", line 3
    file="C:\User\lance\Documents\*.txt"
        ^
SyntaxError: (unicode error) 'unicodeescape' codec can't decode bytes in positio
n 2-3: truncated \UXXXXXXXX escape

C:\Users\lance\Downloads>

fixed the above with

#copy files and folders of Dir
import os
file="C:\\User\\lance\\Documents\\*.txt"
dfile="C:\\Users\\lance\\Documentss\\Documents"
os.system('copy "file" "dfile"')

now I get the error
C:\Users\lance\Downloads>python test.py
The system cannot find the file specified.

---

### Post by Odexios on 2015-02-14
Just a suggestion; instead of using [FONT=courier new]os.system[/FONT], which relies on the shell underneath, use the functions from [shutil]("https://docs.python.org/3/library/shutil.html"), which are platform independent.

Also, instead of escaping the backslash, you can use a raw string: r"C:\...\"

---

### Post by steeldriver on 2015-02-14
is it a simple typo?
> **lance bermudez said:**
> 
```

#copy files and folders of Dir
import os
file="C:\\[COLOR=#ff0000]**User**[/COLOR]\\lance\\Documents\\*.txt"
dfile="C:\\**Users**\\lance\\Documents[COLOR=#ff0000]**s**[/COLOR]\\Documents"
os.system('copy "file" "dfile"')

```

now I get the error
```
C:\Users\lance\Downloads>python test.py
The system cannot find the file specified.
```


---

### Post by ofnuts on 2015-02-14
[QUOTE=Odexios;13228083Also, instead of escaping the backslash, you can use a raw string: r"C:\...\"[/QUOTE]

In fact you can just as well use forward slashes, the Windows APIs accept both (even if they only return backslashes). And the command lines doesn't like forward slashes because they clash with the parameters but when there is no ambiguity forward slashes also work. For instance this works in a WinXP command prompt:
```

dir "/Windows/System32/drivers/etc"

```

---

### Post by lance bermudez on 2015-02-15
I can get this to work
import shutil 
file="C:\\Users\\lance\\Documents\\number.txt"
dfile="C:\\Users\\lance\\Documents\\Document ss"
shutil.copy(file, dfile)

but I want to be able to use *.txt to copy all of the text files not just number. when I use the * I get
C:\Users\lance\Downloads>python test4.py
Traceback (most recent call last):
  File "test4.py", line 4, in <module>
    shutil.copy(file, dfile)
  File "C:\Python34\lib\shutil.py", line 228, in copy
    copyfile(src, dst, follow_symlinks=follow_symlinks)
  File "C:\Python34\lib\shutil.py", line 107, in copyfile
    with open(src, 'rb') as fsrc:
OSError: [Errno 22] Invalid argument: 'C:\\Users\\lance\\Documents\\*.txt'

found this on line and I can't seem to get it to work either
import shutil
import os
source = os.listdir("C:\\Users\\lance\\Documents")
destination = "C:\\Users\\lance\\Documents\\Documentss"
for files in source:
    if files.endswith(".txt"):
        shutil.copy(files,destination)
C:\Users\lance\Downloads>python test4.py
Traceback (most recent call last):
  File "test4.py", line 7, in <module>
    shutil.copyfile(files,destination)
  File "C:\Python34\lib\shutil.py", line 107, in copyfile
    with open(src, 'rb') as fsrc:
FileNotFoundError: [Errno 2] No such file or directory: 'avgnotes.txt'

---

### Post by ofnuts on 2015-02-15
os.listdir() returns only the names of the files in the directory, not complete paths to them. If you use these names directly in the copy command, they are assumed to refer to files in the current director. So either:
[LIST]
[*]you make the source directory the current directory (os.chdir(), and list its contents (os.listdir('.'))
[*]you stay in your current directory, but prefix all file names with the source directory name when copying them.
[/LIST]

---

### Post by lance bermudez on 2015-02-25
Sorry for being so late in getting back but could you give me an example with the os.listdir() and os.chdir() please.

import os
print('current dir')
os.listdir('.')
print('home dir')
os.listdir('/home/lance')

shows
current dir
home dir

but not what is in them.

---

### Post by ofnuts on 2015-02-26
In my C:\Python2.7 directory:
```

>>> import os

>>> os.getcwd()
'C:\\Python27'

>>> os.listdir('.') # list current directory
['DLLs', 'Doc', 'include', 'Lib', 'libs', 'LICENSE.txt', 'NEWS.txt', 'python.exe', 'pythonw.exe', 'README.txt', 'tcl', 'Tools', 'w9xpopen.exe']

>>> os.listdir('libs') # list another directory
['bz2.lib', 'libpython27.a', 'pyexpat.lib', 'python27.lib', 'select.lib', 'unicodedata.lib', 'winsound.lib', '_bsddb.lib', '_ctypes.lib', '_ctypes_test.lib', 
'_elementtree.lib', '_hashlib.lib', '_msi.lib', '_multiprocessing.lib', '_socket.lib', '_sqlite3.lib', '_ssl.lib', '_testcapi.lib', '_tkinter.lib']

>>> os.chdir('libs') # Making that directory the current directory

>>> os.getcwd()
'C:\\Python27\\libs'

>>> os.listdir('.') # Listing the contents of the current directory (same result as above)
['bz2.lib', 'libpython27.a', 'pyexpat.lib', 'python27.lib', 'select.lib', 'unicodedata.lib', 'winsound.lib', '_bsddb.lib', '_ctypes.lib', '_ctypes_test.lib', 
'_elementtree.lib', '_hashlib.lib', '_msi.lib', '_multiprocessing.lib', '_socket.lib', '_sqlite3.lib', '_ssl.lib', '_testcapi.lib', '_tkinter.lib']

```

---

