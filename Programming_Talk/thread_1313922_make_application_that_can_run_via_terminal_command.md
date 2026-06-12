---
title: "make application that can run via terminal command?"
date: 2009-11-04
forum: Programming Talk
---

### Post by baskar007 on 2009-11-04
how to make my python application run via application name as its terminal command? 

for example: 
if i type google-chrome on terminal it will open chrome browser.

---

### Post by 0cton on 2009-11-04
give it executable privileges (chmod +x ) (logically)
don't forget about the shebang (#! /usr/bin/env python at first line)
and copy it to /usr/bin/ (you need root to be able to do it)

---

### Post by A_Fiachra on 2009-11-04
Don't do that!



Keep a local directory of python programs.

chmod 750 <myprog.py>
./myprog.py

If you clutter the /usr/bin directory with your own executables, you will end up screwing yourself.

The idea is you run your stuff from under your home directory, do not include '.' in your PATH, don't copy executables to a directory in your PATH -- unless you really know what you are doing, and you don't yet.

---

### Post by ve4cib on 2009-11-04
If it's something universally-useful, that all users on your system would want to use then putting in PATH somewhere isn't an all-together horrible idea.  I'd advise using /usr/local/bin instead of /usr/bin though.  /usr/local/bin tends to contain less stuff, and you're less-likely to accidentally mess things up there.

If it's something only you will ever be using (either because you're the only user, or because it's just very tailor-made to suit you) you can create a bin directory in your home folder and add that to your path.

```

mkdir ~/.bin         #I like keeping my personal bin directory hidden
cp myProg.py ~/.bin  #copy your program into .bin
chmod -R 700 ~/.bin  #make .bin and its contents executable

```

Finally you need to add .bin to your PATH.  Edit ~/.bashrc (assuming you use bash).  At the end of the file add a line that reads

```
export PATH=/home/myUserName/.bin:$PATH
```

---

### Post by liquidbee on 2009-11-04
> **A_Fiachra said:**
> Don't do that!



Keep a local directory of python programs.

chmod 750 <myprog.py>
./myprog.py

If you clutter the /usr/bin directory with your own executables, you will end up screwing yourself.

The idea is you run your stuff from under your home directory, do not include '.' in your PATH, don't copy executables to a directory in your PATH -- unless you really know what you are doing, and you don't yet.

That's for what /usr/local/bin is there.

---

### Post by baskar007 on 2009-11-05
> **liquidbee said:**
> That's for what /usr/local/bin is there.
So if i put my program into "usr/local/bin",i can call that program by terminal of Alt+F2 ?

---

### Post by liquidbee on 2009-11-05
> **baskar007 said:**
> So if i put my program into "usr/local/bin",i can call that program by terminal of Alt+F2 ?

Yes.

---

### Post by Druke on 2009-11-05
I'm going to have to recommend ve4cib's method, that is the cleanest way to do it.

---

