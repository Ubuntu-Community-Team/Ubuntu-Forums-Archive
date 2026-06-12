---
title: "How do I install Open Real Time Strategy (ORTS)?"
date: 2008-12-23
forum: Programming Talk
---

### Post by Coder543 on 2008-12-23
I tried making it, but when the make began it gave me the strange error of 

"makefile:259: *** "!!!!! unknown OSTYPE= !!!!".  Stop."

Am i in need of exporting some variable, or is there a bug in the makefile that doesn't let it work with ubuntu? I would like to work on developing games, and looking at ORTS might benefit me.

Also, to download ORTS (code only):
svn co svn://anonymous@bodo1.cs.ualberta.ca:/all/pubsoft/orts 
svn co svn://anonymous@bodo1.cs.ualberta.ca:/all/pubsoft/orts_data 
password is guest (for the anonymous account)

Please, Help!

---

### Post by Coder543 on 2008-12-23
Bump. An answer? I seriously don't ask that difficult of questions....

---

### Post by matja on 2008-12-23
Hi Coder543,

A good place to start when building a new project is the README file or maybe INSTALL. In this case it instructs the user to check the makefile for information about setting OSTYPE. At the top of the makefile you'll find the instructions you're looking for.

The problem is that the environment variable OSTYPE is set to "linux-gnu" (at least on my Ubuntu system) and the makefile checks for just plain "linux". The simplest way to remedy this is to run
```
OSTYPE=linux make
```
in the terminal instead of just "make". Be sure that you fulfill all the other requirements mentioned in the README file as well, I saw that there were a bunch of them.

Hope this helps!

Regards, Mattias

---

### Post by Coder543 on 2008-12-23
That did help... a bit. However I am confused by this: "libs/ai/movement/src/Movement.H:37:30: error: boost/function.hpp: No such file or directory"

Shouldn't ORTS *include* that file? Or is there some really obvious thing I am not knowing to do?

---

### Post by TheSpook on 2009-07-22
The thread is old, but maybe this response will help.

Open the README file in ORTS/trunk/.  It'll give you directions on what you need to install.

Note that it mentions running a premade script to grab all dependencies on Ubuntu systems (hurray!)

In ORTS/trunk/config/, type:

```

sudo ./installdeps.ubuntu804.sh

```

Wait for apt to do its thing.

Next, (still reading the README), note that it requires

```

sudo OSTYPE=linux make init

```

run once, to create some directories.  That is your problem.

After this, try the

```

sudo OSTYPE=linux make

```

mentioned above to execute a full compile.

---

### Post by Coder543 on 2009-07-24
ok, cool... only it *is *a little bit too late. I've spent a lot of the summer mastering the use of NGE (NuSoftware Game Engine) which, in turn, uses Irrlicht and IrrKlang.

---

### Post by TheSpook on 2009-07-28
It sounds like ORTS is good for what it's meant to do -- provide an easy to use, OSS RTS platform for AI agent modeling.

And use OGRE!  It has a great user-base, great documentation . . . :).

---

### Post by Coder543 on 2009-07-28
*irrlicht* has a great community and set of documentation. lol, both of our opinions are probably biased... but I like Irrlicht.

---

