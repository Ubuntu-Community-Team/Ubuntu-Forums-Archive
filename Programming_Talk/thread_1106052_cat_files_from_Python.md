---
title: "cat files from Python"
date: 2009-03-25
forum: Programming Talk
---

### Post by sambarluc on 2009-03-25
Hi everybody,
I have a new question for you. I recently started to write some script in Python, but I have a problem that I can't manage to work out.
I need to 'cat' a bunch of (binary) files into a new one, so I wrote something like this:

```
import subprocess as S

F = open('out.dat','w')
output =S.Popen(['cat','in?.dat'],shell=True,stdout=F)
F.close()
```

but I get nothing in the out.dat file. I had also a check with two simple text files, but again nothing.

Where am I wrong?
Thanks

---

### Post by imdano on 2009-03-25
Pass a string instead of a list of arguments ```
output =S.Popen('cat in?.dat', shell=True, stdout=F)
```You only want to pass a list like that if shell=False.

---

### Post by ghostdog74 on 2009-03-25
don't shell out for no reason. You are using Python, therefore, do them all in Python. To open a file in binary and read them all into memory
```

open("file","rb").read()

```
to concatenate them, just do normal string concatenation using "+" operator. There is absolutely no need to call shell's cat command

---

### Post by wmcbrine on 2009-03-25
> **ghostdog74 said:**
> to concatenate them, just do normal string concatenation using "+" operator.That could use an awful lot of RAM, depending on the files. But, yeah, don't shell out to cat; that's silly.

The shutil module might be of use here.

---

### Post by ghostdog74 on 2009-03-25
> **wmcbrine said:**
> That could use an awful lot of RAM, depending on the files. But, yeah, don't shell out to cat; that's silly.

that's only 1 way (in currents times, RAM is cheap). you could use normal file i/o as well, appending data as you write to file

---

### Post by Can+~ on 2009-03-25
Maybe [FileInput]("http://docs.python.org/library/fileinput.html")? Set the whole directory ([FONT="Courier New"]os.listdir(os.getcwd()[/FONT]), filter it ([FONT="Courier New"].endswith(".dat")[/FONT]) and append ([FONT="Courier New"]open("myfile", "a")[/FONT]) it to a new file?

---

### Post by ghostdog74 on 2009-03-25
> **sambarluc said:**
> Hi everybody,
I have a new question for you. I recently started to write some script in Python, 
if Python is not a must, do it in the shell
```

# cat *.dat > newfile

```
that's it.

---

