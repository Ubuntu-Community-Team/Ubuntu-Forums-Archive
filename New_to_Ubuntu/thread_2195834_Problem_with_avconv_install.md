---
title: "Problem with avconv install"
date: 2013-12-26
forum: New to Ubuntu
---

### Post by egboss001 on 2013-12-26
im trying to install avconv
```

user@ubuntu:~$ sudo apt-get install avconv
[sudo] password for user: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package avconv

```


E: Unable to locate package avconv

---

### Post by oldos2er on 2013-12-26
I'm guessing you found what you needed in the *ffmpeg* package. In the future if you're going to mark your thread 'Solved' please include the solution as a courtesy to others.

---

### Post by ajgreeny on 2013-12-26
For anyone else looking, avconv is just one of this list of executables in the libav-tools package.

/usr/bin/avconv
/usr/bin/avplay
/usr/bin/avprobe
/usr/bin/avserver
/usr/bin/ffmpeg
/usr/bin/ffplay
/usr/bin/ffprobe
/usr/bin/ffserver
/usr/bin/qt-faststart

But as oldos2er said, it's a pity the OP didn't say so himself.

---

### Post by andrew.46 on 2014-01-05
> **ajgreeny said:**
> 

```

/usr/bin/ffmpeg
/usr/bin/ffplay
/usr/bin/ffprobe
/usr/bin/ffserver

```


These would be symlinks I imagine?

---

