---
title: "Python TarFile.add question"
date: 2009-10-09
forum: Programming Talk
---

### Post by tjpren on 2009-10-09
Hello Forum,

Does anyone know the format that the exclude function takes in the Python TarFile.add as shown:

TarFile.add(name, arcname=None, recursive=True, exclude=None)

The documentation says that it must be a function or parameter, but I've not found anything that works.

I'm using Python 2.6

Regards

---

### Post by unutbu on 2009-10-09
This creates test.tar out of a directory called testdir. It excludes all files in testdir that end with '~'.

[PHP]#!/usr/bin/env python
import tarfile
tarname='test.tar'
adir='testdir'
tar=tarfile.open(tarname,'w')
def exclude_tilde(filename):
    return filename.endswith('~')
tar.add(adir,exclude=exclude_tilde)
tar.close()
[/PHP]

From [http://docs.python.org/library/tarfile.html#module-tarfile](http://docs.python.org/library/tarfile.html#module-tarfile)
> If exclude is given it must be a function that takes one filename argument and returns a boolean value. Depending on this value the respective file is either excluded (True) or added (False).

---

### Post by tjpren on 2009-10-10
Much appreciated - thank you very much.

---

### Post by tjpren on 2009-10-10
unutbu,

That works really well.  I can even add extra filters with something like :
return filename.endswith('~') or filename.endswith('mp3').

Any ideas how to exclude whole directories, rather than filter all files based on their extension ?

Thanks

---

### Post by unutbu on 2009-10-10
If you put a print statement in exclude_tilde
[PHP]
def exclude_tilde(filename):
    print(filename)
    return filename.endswith('~') [/PHP]

you'll see that a long path name is passed to the variable filename.
Directories as well as files are passed to exclude_tilde.
So you could filter out a directory like this:
[PHP]
def exclude_tilde(filename):
    return (('/baddir' in filename) or 
            filename.endswith('~')
            )		[/PHP]

---

### Post by tjpren on 2009-10-10
Absolutely brilliant - thanks heaps.

I was looking at something along the lines of

for filename in os.listdir('/dirx'):
return filename

but that was not getting me anywhere.  Your suggestion is really very straightforward.

I'm writing my own file backup program and at the same time learning a little about python.  I know there is code already out there, but I'm learning by doing.

Again, much appreciated for the help.

---

