---
title: "JMF installation problem -- no jmv4l in java.library.path?"
date: 2010-11-09
forum: Programming Talk
---

### Post by masqueradestar on 2010-11-09
Hi all.

I was given code that uses JMF -- for research, so I'm stuck with it -- and I can't seem to figure out how to fix this error. I'm running Ubuntu 9.10 32-bit, and my IDE is Eclipse.

After fixing the tail problem ([https://bugs.edge.launchpad.net/ubuntu/+bug/104511](https://bugs.edge.launchpad.net/ubuntu/+bug/104511)), installing, and importing the .jars into the path, when I try to run the program, I get this:

```
JavaSound Capture Supported = true
JavaSoundAuto: Committed ok
java.lang.UnsatisfiedLinkError: JMFSecurityManager: java.lang.UnsatisfiedLinkError: no jmv4l in java.library.path
java.lang.NoClassDefFoundError: Could not initialize class com.sun.media.protocol.v4l.V4LCapture
```


All my google-fu has failed me; I can't find anything about jmv4l or how to include it in the path. Does anyone with more knowledge than me know what I did wrong, or what I need to do to fix this?

---

### Post by spjackson on 2010-11-09
Did you get jmv4l.so (32-bit) from somewhere?  Where did you install it?

---

### Post by masqueradestar on 2010-11-09
> **spjackson said:**
> Did you get jmv4l.so (32-bit) from somewhere?  Where did you install it?

I can't find jmv4l.so anywhere -- only libjmv4l.so, which apparently isn't the right thing? The contents of the lib folder are as such:

```
x@x:~/Code/JMF-2.1.1e$ ls -a lib/
.                    libjmdaud.so     libjmjpeg.so   libjmxlib.so
..                   libjmfjawt.so    libjmmpa.so    mediaplayer.jar
jmf.jar              libjmg723.so     libjmmpegv.so  multiplayer.jar
jmf.properties       libjmgsm.so      libjmmpx.so
jmf.properties.orig  libjmh261.so     libjmutil.so
libjmcvid.so         libjmh263enc.so  libjmv4l.so
```

---

### Post by spjackson on 2010-11-09
My mistake, libjmv4l.so is probably what it's looking for. You can set the library path if you run java from the command line
```

java -Djava.library.path=./lib

```I don't know how you do that in Eclipse though, I'm afraid.

---

### Post by masqueradestar on 2010-11-09
For anyone more familiar with Eclipse than me, on the project I'm working on, from right click > Properties > Java Build Path > Source > Native library location, chose the lib folder and tried again. This time, I got:

```
JavaSound Capture Supported = true
JavaSoundAuto: Committed ok
java.lang.UnsatisfiedLinkError: JMFSecurityManager: java.lang.UnsatisfiedLinkError: /home/jvirdo/Code/JMF-2.1.1e/lib/libjmv4l.so: libjmutil.so: cannot open shared object file: No such file or directory
java.lang.NoClassDefFoundError: Could not initialize class com.sun.media.protocol.v4l.V4LCapture
```

libjmutil.so is in JMF-2.1.1e/lib, but it seems to be... looking in libjmv4l.so for another .so file? :\

---

### Post by spjackson on 2010-11-09
Hmm... maybe set LD_LIBRARY_PATH
```

LD_LIBRARY_PATH=/home/jvirdo/Code/JMF-2.1.1e/lib/
export LD_LIBRARY_PATH

```

---

### Post by masqueradestar on 2010-11-09
> **spjackson said:**
> Hmm... maybe set LD_LIBRARY_PATH
```

LD_LIBRARY_PATH=/home/jvirdo/Code/JMF-2.1.1e/lib/
export LD_LIBRARY_PATH

```

Just tried it, but I got the same error. Thanks, though.

---

### Post by Norwegian-Blue on 2011-03-07
Did you ever fix this ? 
I am struggling with the same problem now.

Many thanks
Ian

---

### Post by masqueradestar on 2011-03-07
> **Norwegian-Blue said:**
> Did you ever fix this ? 
I am struggling with the same problem now.

Many thanks
Ian

Unfortunately, no... I gave up and switched to another computer I have running Windows 7.

---

### Post by Norwegian-Blue on 2011-03-08
Right, just worked it out.

It has to do with the LD_LIBRARY_PATH environment variable.

It seems (although I am no Linux expert) that if a system library loads  another library, this has to be in one of the "correct" places. If it is  not, then it can be found by setting the LD_LIBRARY_PATH.

So if you want to run JMF from Eclipse, you have to do two things:


[LIST=1]
[*]Set the native library location for the jmf.jar file. Project - properties - Java Build Path - Libraries tab - expand the jmf.jar item - Native library location: - Press the Edit button on the right hand side
[*]When you run your application, you must set the LD_LIBRARY_PATH in the launch configuration. This is under the "Environment" tab. Name = LD_LIBRARY_PATH value = <path to where the .so files are>
[/LIST]
Once I did this, I could run JMFInit from within Eclipse.

Ian

---

