---
title: "How to specify path in Python?"
date: 2009-04-28
forum: Programming Talk
---

### Post by StunnerAlpha on 2009-04-28
Ey guys, I have a really noob question and I have googled and surprisingly couldn't find an example or tutorial that clearly showed how to do this, I am sure I can figure it out if I kept at it, but I really can't afford to waste time trying all the possibilities. This is what I have tried to do:
```

$ python
Python 2.5.2 (r252:60911, Jul 31 2008, 17:28:52) 
[GCC 4.2.3 (Ubuntu 4.2.3-2ubuntu7)] on linux2
Type "help", "copyright", "credits" or "license" for more information.
>>> import os
>>> artist = "rancid"
>>> os.makedirs("Artists")
>>> os.makedirs(Artists/artist)
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
NameError: name 'Artists' is not defined
>>> os.makedirs("Artists"/artist)
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
TypeError: unsupported operand type(s) for /: 'str' and 'str'

```
I am trying to specify the path in which a directory should be created. Thanks for all the help in advance. Also I have a part two to this question which is, what command would I use to put files into the directory afterwards? Thanks again.

---

### Post by G|N| on 2009-04-28
> **StunnerAlpha said:**
> 
```

>>> import os
>>> artist = "rancid"
>>> os.makedirs("Artists")
>>> os.makedirs("Artists"/artist)

```


This should be:
```

>>> import os
>>> artist = "rancid"
>>> os.makedirs("Artists")
>>> os.makedirs("Artists/" + artist)

```

---

### Post by benj1 on 2009-04-28
to answer your second question 

```
file = open('path/to/file/new_file','w')
file.write('words')
file.close()
```

read the stickies for some good tutorials on python

---

### Post by StunnerAlpha on 2009-04-28
Thank you very much good sirs!

---

### Post by G|N| on 2009-04-28
Do you want to copy the files in the newly created directory or only write a new text file?
There is a big difference!

---

### Post by StunnerAlpha on 2009-04-28
Hm, I am trying to get this to work but I can't figure it out. Here is my code:
```

#!/usr/bin/python
import eyeD3, re, os, shutil
...
os.makedirs("Artists/" + artist)
dir_src = os.getcwd()
dir_dst = (dir_src + "/Artists/" + artist)
src_file = os.path.join(dir_src, file)
dst_file = os.path.join(dir_dst, file)
shutil.move(src_file, dst_file)
...

```

And here are the errors I am getting:
```

a$ python decipher-rename4-27-09.py 
Traceback (most recent call last):
  File "decipher-rename4-27-09.py", line 19, in <module>
    src_file = os.path.join(dir_src, file)
  File "/usr/lib/python2.5/posixpath.py", line 60, in join
    if b.startswith('/'):
AttributeError: type object 'file' has no attribute 'startswith'

```

Any help really appreciated! Thanks.

---

### Post by StunnerAlpha on 2009-04-28
> **G|N| said:**
> Do you want to copy the files in the newly created directory or only write a new text file?
There is a big difference!
I want to move the files that are in the current directory to the newly created directory which will be a directory created in the "Artists" folder named after the file name's artist(don't worry I have the artist name determining part all sorted out).

---

### Post by ghostdog74 on 2009-04-28
dude, look at the error message. it says it all . file has no attribute startswith. that means your "file" variable is something wrong. And don't name your variable "file", because "file" is internal to Python. Its used to open a file handler. check where your file variable is defined and make sure its defined. from your previous posts, i guessed you are just starting out with Python (from shell), so i suggest you read the documentation for the basics.

---

### Post by red_Marvin on 2009-04-28
I believe that the recommended way, is to avoid path separators alltogether and use os.path.join() directly, in order to be cross platform, since different platforms [may] use different characters for separation:
```
>>> import os
>>> pathstuff = ["foo","bar","baz"]
>>> os.path.join(*pathstuff)
'foo/bar/baz'
```

---

### Post by StunnerAlpha on 2009-04-28
Thanks guys, got it.

---

