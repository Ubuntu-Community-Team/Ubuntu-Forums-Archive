---
title: "tarfile and Python"
date: 2006-10-20
forum: Programming Talk
---

### Post by thomasaaron on 2006-10-20
Hello, all.

I'm trying to use Python to create a tar file of my home directory: /home/thomasaaron

When I use the following code:

[PHP]import tarfile
tar = tarfile.open("backup.tar", "w")
tar.add('home/thomasaaron')
tar.close()[/PHP]

...it puts all of the FILES in /home/thomasaaron into the tar file, but it does not delve into the other DIRECTORIES that are contained therein.

Can someone help me figure out how to get it to be completely recursive and copy EVERYTHING in /home/thomasaaron (subdirectories and all)?

Thanks for your help.

Best,
Tom

---

### Post by ghostdog74 on 2006-10-21
you can try using os.walk(dir) and then using the loop to add the files..

eg

for r,d,f in os.walk(dir):
  ... # tar code
  ....
  t.add(f)

OR

from the docs:
> add(  	name[, arcname[, recursive]])
    Add the file name to the archive. name may be any type of file (directory, fifo, symbolic link, etc.). If given, arcname specifies an alternative name for the file in the archive. Directories are added recursively by default. This can be avoided by setting recursive to False; the default is True.


The add() method can do recursive..

---

### Post by thomasaaron on 2006-10-21
Thanks.  I'll try the walk() method.

I read that other piece in the documentation. I'm understanding it to say that it is, by default, set to be recursive and dig into all of the subdirectories, but it doesn't seem to be working.

I tried to set in on 'True' as well. But no dice.

I'll let you know how the walk() works out.

Beest,
Tom

---

### Post by ghostdog74 on 2006-10-21
in fact, i think its tar.add('home/thomasaaron') 
it should be 

tar.add('/home/thomasaaron')

---

