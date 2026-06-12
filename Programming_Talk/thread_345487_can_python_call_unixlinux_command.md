---
title: "can python call unix/linux command ?"
date: 2007-01-24
forum: Programming Talk
---

### Post by moonhk on 2007-01-24
In shell script can using unix/linux command. How about python can call unix/linux command ?

In my shell script change *.jpg to 2007*.jpg , Can python do like below ?

ymd=`date +%Y%m%d`
tmp=_file.txt

echo ymd=$ymd
ls *.jpg > ${tmp}
while read -r r
do
   chk=${r:0:4}
   if [[ ! ${chk} == "2007" ]] ; then
     echo ${r} ${r%%.jpg} $chk
     mv $r ${ymd}_${r}
   fi
done < ${tmp}
rm ${tmp}

---

### Post by duff on 2007-01-24
There's an os.rename, if you just want to rename files.  But, in general, you can call any process using os.system

```
>>> import os
>>> print os.rename.__doc__
rename(old, new)

Rename a file or directory.
>>> os.system('echo "Hello, World!"')
Hello, World!
0
>>> 

```

---

### Post by jblebrun on 2007-01-24
As the other replier mentioned, in this case, you just want to use os.rename()

In addition to os.sytem, you can do more complex things, to, using os.popen 
(and also popen2, popen3, popen4...)

os.popen allows you to execute another command in a non-blocking fashion, and read the output of the program into python variables. So you can write something like:

```

p = os.popen('ls')
for line in p.readlines():
     print p

```

Of course, in this simple example, the execution blocks at p.readlines until the command is done, but you can use more detailed file polling/reading methods to avoid that.

---

### Post by moonhk on 2007-01-24
Tried. OK. I try to learn about python.

Try using IDEL , the echo seem not work.
**Output in IDEL** 
IDLE 1.1.3      ==== No Subprocess ====

>>> import os
>>> os.system('echo "HELLO"')
0
>>> 

Try on DrPython
# unix.py
import os
os.system('echo "hello"')
p = os.popen('ls /home/moonhk')
for line in p.readlines():
	print** line**

**Output on DrPython editor.**

usr/bin/python -u  "/home/moonhk/python/unix.py"
hello
award

cpp

data

Desktop

eclipse_error.txt

gcc

homephotos

internet_photos

javaux

lamp

python

shell

workspace

www

---

### Post by jblebrun on 2007-01-24
I'm not sure why it doesn't work properly in IDLE. My guess is that the IDLE interpreter is not a proper shell, and so the output from os.system gets sent to some other output screen. I'm not sure, because I've never used IDLE.

But os.popen should still give the expected results in IDLE, give that a try.
p=os.open('echo hello')
print p.readline()

---

### Post by wsonar on 2009-04-29
Is there a similar command to invoke nautilus not necessarily if I where to type nautilus but more like a browse for file button?

---

### Post by DocForbin on 2009-04-29
fwiw, os.popen is deprecated, use the subprocess module unless you have a very old python (< 2.4)

[http://docs.python.org/library/subprocess.html#module-subprocess](http://docs.python.org/library/subprocess.html#module-subprocess)

edit: I just noticed this thread is over 2 years old....

---

### Post by wsonar on 2009-04-29
> **DocForbin said:**
> fwiw, os.popen is deprecated, use the subprocess module unless you have a very old python (< 2.4)

[http://docs.python.org/library/subprocess.html#module-subprocess](http://docs.python.org/library/subprocess.html#module-subprocess)

edit: I just noticed this thread is over 2 years old....

Cool Thanks for the info..

---

### Post by wsonar on 2009-04-29
Yea I noticed it was an old thread, don't know how I came across It

---

### Post by konjeng on 2010-06-01
how to use "curl" in python script?

---

### Post by StephenF on 2010-06-01
> **konjeng said:**
> how to use "curl" in python script?

For access to libcurl the python bindings, pycurl. The subprocess module for running the command line curl program.

---

