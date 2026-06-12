---
title: "Pass arguemtn through os.system call in python?"
date: 2008-03-26
forum: Programming Talk
---

### Post by xelapond on 2008-03-26
Hello everyone, 

I am proof of concept driver for a gyro mouse I am building.  If the concept works I am going to write a much better driver, but this will work for now.

So, how would I go about passing a variable through this bit of python code:

```
os.system(xte "mousermove NUMBER0 NUMBER1")
```

Where NUMBER0 and NUMBER1 are different variables.

Sorry if this is an obvious question answered by the documentation, but I couldn't find it.

Thanks, 

Alex

---

### Post by LaRoza on 2008-03-26
os.system() takes a sring.

So you just pass it a string.

os.system(xte + "  mousermove " + NUMBER0 + " " + NUMBER1)

---

### Post by pmasiar on 2008-03-26
> **xelapond said:**
> 
```
os.system(xte "mousermove NUMBER0 NUMBER1")
```


xte is name of the utility to run? Assuming NUMBER0 NUMBER1 are integers, something like:

```
os.system("xte mousermove %i %i" % (NUMBER0 NUMBER1) )
```
 
If mousermove is variable, use same trick [string interpolation](http://docs.python.org/lib/typesseq-strings.html), you need to get a string with all values in proper places.

Also, your naming is wrong, read about [Python standards](http://ubuntuforums.org/showthread.php?t=618742) - start with [PEP0008](http://www.python.org/dev/peps/pep-0008/)

---

### Post by LaRoza on 2008-03-26
> **pmasiar said:**
> xte is name of the utility to run? Assuming NUMBER0 NUMBER1 are integers, something like:

```
os.system("xte mousermove %i %i" % (NUMBER0 NUMBER1)
```
 


Don't forget to close the () for os.system().

---

### Post by pmasiar on 2008-03-26
Thanks, it was a typo, fixed now.

---

### Post by LaRoza on 2008-03-26
> **pmasiar said:**
> Thanks, it was a typo, fixed now.

I do it all the time, when having parentheses in function calls. I think it is my most common error.

---

