---
title: "[SOLVED] Embarrassingly stupid $PATH question"
date: 2008-11-08
forum: New to Ubuntu
---

### Post by heartsensei on 2008-11-08
I am using AMD64 Intrepid. I installed SUN's JDK version 6 through synaptic package manager. I modified a file somewhere on the system to make $PATH=/usr/local/jdk/bin;$PATH. This is unfortunately not the correct path to the JDK binaries. Now I can't remember which file I modified. I have checked all the obvious ones. /etc/bash.bashrc etc...
I have a totally vanilla Ubuntu setup, is there a list of standard places where the $PATH can be modified or is there a grep command I can use to search everything for the change? Is there something which tracks/audits changes to the $PATH as it boots up? Thanks in advance.

---

### Post by cmnorton on 2008-11-08
In your /home/<you> directory, did you check

.profile
.bash_profile
.bashrc

---

### Post by Anothermindbomb on 2008-11-08
I'd begin looking in ~/.profile

---

### Post by lswest on 2008-11-08
I've installed the sun-java6-jdk on my 32 bit system, and I didn't have to change the path variable like you do in windows, are you sure you need to for your 64 bit?

To answer your question the $PATH variable is declared in /etc/profile and ~/.profile (also .bashrc and .bash_profile I think).

You can probably also do:
```
echo $PATH
export $PATH="<values for the path>"
``` I'm just thinking out loud with that command, someone would need to test it.

---

### Post by heartsensei on 2008-11-08
Thanks very much for the help, it was indeed in /home/<me>/.profile
I guess I didnt check all the obvious places after all :-)

---

