---
title: "Setting ARGV[0] in python2.3"
date: 2009-09-21
forum: Programming Talk
---

### Post by openfly on 2009-09-21
How is one supposed to set ARGV[0] in python 2.3?

Is there a method that transcends the growing tree of python versions?

---

### Post by wmcbrine on 2009-09-21
I would say, in general, that one is not supposed to set sys.argv. Why do you want to do this?

However, these work perfectly well:

```
sys.argv = ['hello']
```
```
sys.argv[0] = 'foo'
```

in 2.3 or, probably, any other version.

---

### Post by Bachstelze on 2009-09-21
You don't normally set argv[0] (or any other element of argv) yourself. The interpreter automatically sets it to the name by which the script was called.

That being said, you can of course change its value to an arbitrary one, like you would with any other variable:

```
sys.argv[0] = "foo"
```

---

### Post by ve4cib on 2009-09-21
A couple of interpretations of what you're asking...

1- you want to change sys.argv[0] in-code.  See the above two replies for that.

2- you want to set the value of sys.argv[0] *before* you execute any of the rest of your code (i.e. using it for user-input).  In this case sys.argv[0] is the first space-separated element in the command you executed to start the Python script.

For example, if you executed:

```
$ python myscript.py --help
```

the shell would assign sys.argv is equal to

```
['python', 'myscript.py', '--help']
```

Similarly if you executed

```
$ ./myscript.py --help
```

sys.argv would be:

```
['./myscript.py', '--help']
```

Hopefully something in between the earlier posts and this one will answer your question.  If not please clarify what it is you're wanting to do.

---

### Post by openfly on 2009-09-21
no.

I misexpressed myself.

What I am looking to do is something like os.setprocname()

I want to set the process name of the script after it's begun to execute.  This should be possible in posix and most languages have a function for it.

In perl it would be $0 = "process name";

The end result would be to hide the arguments and subsequent switches in any process list.

Thoughts?

---

### Post by wmcbrine on 2009-09-21
> **ve4cib said:**
> For example, if you executed:

```
$ python myscript.py --help
```

the shell would assign sys.argv is equal to

```
['python', 'myscript.py', '--help']
```Actually that will come out as ```
['myscript.py', '--help']
``` within the script.

---

### Post by openfly on 2009-09-21
So I tried this approach:

```

import dl
libc = dl.open('/lib/libc.so.6')
libc.call('prctl', 15, 'faked process\0', 0, 0, 0)

```

But, looks like dl isn't 64bit friendly.
Still hunting.

Caveat:  Can't modify my python environment... it's "special".  Modification to it is disallowed.

---

### Post by unutbu on 2009-09-21
Perhaps look at Anonymous's solution dated 2008-06-24:

[http://dannipenguin.livejournal.com/166352.html](http://dannipenguin.livejournal.com/166352.html)
```

>>> import procname
>>> procname.getprocname()
'python'
>>> procname.setprocname('My super-name 9') 
```

This affects both ps and top output.

procname is python library downloadable from [http://code.google.com/p/procname/downloads/list](http://code.google.com/p/procname/downloads/list). 

Warning: I have not vetted the code.

(See also [http://bugs.python.org/issue5672](http://bugs.python.org/issue5672))

---

### Post by Bachstelze on 2009-09-21
> **ve4cib said:**
> 
For example, if you executed:

```
$ python myscript.py --help
```

the shell would assign sys.argv is equal to

```
['python', 'myscript.py', '--help']
```

Wrong.

```
firas@iori ~ % cat argv.py
#!/usr/bin/env python

import sys

print sys.argv
firas@iori ~ % python argv.py --help
['argv.py', '--help']

```

Baww, I got pwn3d. :(

---

### Post by openfly on 2009-09-21
> **unutbu said:**
> Perhaps look at Anonymous's solution dated 2008-06-24:

[http://dannipenguin.livejournal.com/166352.html](http://dannipenguin.livejournal.com/166352.html)
```

>>> import procname
>>> procname.getprocname()
'python'
>>> procname.setprocname('My super-name 9') 
```

This affects both ps and top output.

procname is python library downloadable from [http://code.google.com/p/procname/downloads/list](http://code.google.com/p/procname/downloads/list). 

Warning: I have not vetted the code.

(See also [http://bugs.python.org/issue5672](http://bugs.python.org/issue5672))

Yeah I can't be loading a custom module for something this small.  It'd be impossible to make happen.

---

