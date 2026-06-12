---
title: "[SOLVED] Plug-in Directory"
date: 2008-06-13
forum: New to Ubuntu
---

### Post by expatCM on 2008-06-13
I need to install Aleks.  The install instructions are not so good.  Their technical support is clueless.

Does anyone know where would be the correct directory to put the .jar file mentioned in this link?
[http://www.aleks.com/downloads/linux_jvm](http://www.aleks.com/downloads/linux_jvm)

---

### Post by ibuclaw on 2008-06-13
The command
```
 locate "lib/ext"
```
Reveals that the directory is here:
```
/usr/lib/jvm/java-6-sun-1.6.0.06/jre/lib/ext
```
It is from the "**sun-java6-bin**" package, if you haven't already installed it.


Regards
Iain

---

### Post by expatCM on 2008-06-14
On the money :)

Yes, that worked ....  100%.  Perfect.

Thank you for your help.

---

### Post by Lizard_King on 2008-09-16
How is this solved? Maybe you could share your solution with the rest of us. (in easy to understand steps).

I downloaded the Aleks-Pack, how do I install it.

How could anyone say this is better than Windows?

---

### Post by Lizard_King on 2008-09-16
I tried to save the aleks-pack to the same directory where Java resides, /usr/lib/jvm, but got this error message.

> You do not have permission to create files in this directory.

---

