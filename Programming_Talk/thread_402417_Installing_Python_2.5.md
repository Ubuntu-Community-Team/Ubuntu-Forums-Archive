---
title: "Installing Python 2.5"
date: 2007-04-05
forum: Programming Talk
---

### Post by RyanHLewis on 2007-04-05
Hi, I have Python 2.4 installed via Synaptic. I have run sudo apt-get upgrade many times, and Synaptic DOES NOT have Python 2.5 available for download, additionally on python.org for linux it says check your package manager to install python 2.5. 

Does ubuntu dapper just not support Python 2.5?

How do I get Python 2.5??

---

### Post by PriceChild on 2007-04-05
Ubuntu dapper does not contain Python 2.5

It is available as of Edgy in the python2.5 package.

---

### Post by pmasiar on 2007-04-05
Do you need some special 2.5 features? some of new features you can get using "from __future__ import xxx"

For beginners, it is easier to stick with the version provided by default, because if you change 2.4 to 2.5, or symlink, or something, you may break other system programs expecting 2.4. Libraries and stuff. It is possible to have 2.5, but you need to know what you are doing.

It is easier to upgrade.

---

### Post by gh0st on 2007-04-06
> **pmasiar said:**
> Do you need some special 2.5 features? some of new features you can get using "from __future__ import xxx"

For beginners, it is easier to stick with the version provided by default, because if you change 2.4 to 2.5, or symlink, or something, you may break other system programs expecting 2.4. Libraries and stuff. It is possible to have 2.5, but you need to know what you are doing.

It is easier to upgrade.

I'd say pmasiar is right, unless you need some specific Python 2.5 functions I would stick with 2.4 for now. You could get into a mess with some programs on your system expecting 2.4 possibly. I've found that I can run every program I need to on Python 2.4 or 2.5, I have some development boxes with different versions on them and I move my projects between them without any hassle. I haven't found anything that says it requires 2.5 yet. Maybe I'm missing something though who knows :)

---

### Post by RyanHLewis on 2007-04-06
Ok, I think I may i'm using the pickle procedures, and they aren't working right.. is it possible to upgrade to edgy without much effort? Or is that a huge deal?? I have a dual booted laptop..

---

### Post by pmasiar on 2007-04-06
pickle is working OK for me in 2.4. maybe you have a bug? :-)

---

### Post by maddog39 on 2007-04-06
All you need to do is go to Applications > Accessories > Terminal and type:
```

sudo aptitude install python2.5

```If it doesnt seem to work, let me know. But it should. This should also handle all the new python dependencies and addon libraries that you might have attached to it which were installed via the package manager.

---

### Post by WW on 2007-04-06
He said he is using dapper. python2.5 is not available in the Ubuntu dapper repositories.

---

### Post by RyanHLewis on 2007-04-08
Ok, So I upgraded to Python2.5 and Ubuntu Edgy.

I still recieve the same error, but I am not sure why.

When I use pickle, or cPickle, it tells me that I am missing the module copy_reg, from inside one of the files that runs pickle. (i'm trying to copy the error into the forum)

I thought pickle stuff came with Python, why is it that their dependencies are not properly installed?

---

### Post by RyanHLewis on 2007-04-08
ryan@ryan-laptop:~/Desktop/HSI$ python run.py
Traceback (most recent call last):
  File "run.py", line 7, in ?
    f = targetFinder.targetFinder(header,file,r,p)
  File "/home/ryan/Desktop/HSI/targetFinder.py", line 164, in __init__
    graph = self.open_from_pickle('graph')
  File "/home/ryan/Desktop/HSI/targetFinder.py", line 91, in open_from_pickle
    obj = cPickle.load(f)
[B]ImportError: No module named copy_reg
[/B]

---

### Post by pmasiar on 2007-04-08
Can you show source? I used pickle.dump() and pickle.load() and had no problems, you are doing something tricky like [this](http://www.python.org/doc/1.5.2p2/lib/module-pickle.html),which mentions module copy_reg. Read [example](http://docs.python.org/lib/pickle-example.html) and do simple thing first.

---

### Post by RyanHLewis on 2007-04-08
I will show a small amount, I hope it suffices.
```

import cPickle
import struct
import numpy
import networkx as NX
import Image

```
...
```

	def send_to_pickle(self, obj, filename):
		f = open(filename, 'w')
		cPickle.dump(obj, f)
		f.close()

	def open_from_pickle(self, filename):
		f = open(filename, 'r')
		obj = cPickle.load(f)
		f.close()
	
		return obj


```

---

### Post by menschtx on 2008-05-27
when attempting to add python 2.5 to blender in ubuntu 8.04 I get the error message invalid scrips dir. check console. I can see it in the directory. What must I do?

---

### Post by pmasiar on 2008-05-27
You should start your own thread, your question is 100% unrelated to OP's question :-)

---

