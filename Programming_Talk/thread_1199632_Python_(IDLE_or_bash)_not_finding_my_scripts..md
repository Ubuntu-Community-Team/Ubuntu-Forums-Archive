---
title: "Python (IDLE or bash) not finding my scripts."
date: 2009-06-29
forum: Programming Talk
---

### Post by Armagguedes on 2009-06-29
Hello.

I've just started learning to program with Python 3 (i know, technically it's scripting), using Swaroop's "A Byte of Python".

This is about the 3rd time (iirc) i've started to learn python, and i always have had the same problem. So far i've only written basic Hello Worlds andf a couple of incremental counters with a string.

I always have the same problem. I generally use KATE to write my stuff, and save stuff with a *.py extension (sometimes i put spaces in the filename, does this count?).

If i open the scripts with IDLE's editor and hit RUN, they work fine. However, if i use IDLE by itself or bash on /usr/bin/python3 and try and invoke the scripts, they can't be found.

I save everything into ~/documentia/python/, and have thought of adding said directory to $PATH, but don't want to fiddle too much with system files, unless i have to.

Ideas?
Tks;
b

---

### Post by geirha on 2009-06-29
If its not in PATH, you must either cd to the directory, or provide the path to the script.
```

cd ~/documentation/python/
python myscript

python ~/documentation/python/myscript

# If you've set a hash-bang (first line reading something like #!/usr/bin/env python)
# And the file is executable, then you can invoke directly
~/documentation/python/myscript

```

To add it to your personal PATH, add the following line at the end of ~/.profile
```
PATH="$PATH":~/documentation/python
```
It will take effect next time you log in, and then you can simply type ```
myscript
```

---

### Post by Armagguedes on 2009-07-03
Many thanks, it worked.
That's a relief; now onto coding

Cheers mate;
b

---

### Post by yltang on 2011-06-02
My problem is:

I started IDLE from the directory of my module (let's say the name of the module is 'test.py'). Now, I can do "import test", however, I cannot run the module by directly typing its name "test". The error message was "NameError: name 'test' is not defined". It seems that IDLE cannot find the module. Why is that? Thanks.

---

### Post by HoKaze on 2011-06-03
> **yltang said:**
> My problem is:

I started IDLE from the directory of my module (let's say the name of the module is 'test.py'). Now, I can do "import test", however, I cannot run the module by directly typing its name "test". The error message was "NameError: name 'test' is not defined". It seems that IDLE cannot find the module. Why is that? Thanks.

This is most likely because there's already a module within python called test. I just tried in with python 2.6 and yes, test is a module that already exists on my system. Try renaming your test.py to something less likely to share a name with an existing module and see if the problem persists. Which version of python are you using?
Also, in future, please start your own thread rather than using someone else's.

---

### Post by ThatCoolGuy220 on 2011-06-04
IF solved mark it as solved

it will help people with the same problem find it faster

---

### Post by yltang on 2011-06-08
HoKaze,
I changed the name of the module but the problem was still there. Thanks for your suggestion and I've started another thread for this problem: [http://ubuntuforums.org/showthread.php?p=10918674#post10918674](http://ubuntuforums.org/showthread.php?p=10918674#post10918674)

---

