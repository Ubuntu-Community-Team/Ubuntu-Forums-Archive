---
title: "Installing Software, gcc"
date: 2013-05-30
forum: New to Ubuntu
---

### Post by MichelleH on 2013-05-30
Hi, 
I am new to linux and this forum so I apologize in advance for any mistakes. I am attempting to install an older release of gcc (4.6.3). I downloaded what I think is the pack from the following link, [http://gcc.cybermirror.org/releases/gcc-4.6.3/](http://gcc.cybermirror.org/releases/gcc-4.6.3/). What do I do now? I was looking for something that resembles an executable in the install folder but was unable to. 
Thanks so much for any help!!!

---

### Post by gifford on 2013-05-30
Why not use Synaptic package manager for gcc. Not sure what version of Ubuntu you are using, but synaptic manager has the version you are looking for in 12.04.2 and will do the install for you.
If not familiar with synaptic, you can install it from the Ubuntu Software Center.

---

### Post by Cheesemill on 2013-05-31
First of all get rid of that file you downloaded, you don't need it.

Earlier versions of gcc are in the repositories, you can install 4.6 by running the command...
```
sudo apt-get install gcc-4.6
```

---

### Post by MichelleH on 2013-05-31
Thanks a lot, the "sudo apt-get install gcc-4.6" command worked like a charm.

---

