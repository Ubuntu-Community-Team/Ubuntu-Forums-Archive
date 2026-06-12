---
title: "Help OpenJDK Disappeared"
date: 2009-01-28
forum: Programming Talk
---

### Post by xaegis on 2009-01-28
Yesterday my computer was running fine. Today I tried to compile the Java programs I was working on and I get the message: "javac: not found"
I used:

e******@****s:~$ sudo update-alternatives --config java

There are 4 alternatives which provide `java'.

  Selection    Alternative
-----------------------------------------------
*         1    /usr/lib/jvm/java-6-sun/jre/bin/java
          2    /usr/bin/gij-4.3
 +        3    /usr/lib/jvm/java-gcj/jre/bin/java
          4    /usr/bin/gij-4.2

nowhere do i see the jdk. So i reinstall both the SUN and OPEN jdk after a complete removal in synaptic and still they do not appear.

Anyone have a clue about this? The package installer said it was having some trouble with installing other packages last week. Could It be a corrupted filesystem?

Help!

I have homework that is due for my Java class tomorrow and I have to get it done tonight!!!


Thanks in advance!

-e

---

### Post by kavon89 on 2009-01-29
Having both the Sun and Open versions of the JDK probably isn't a good idea.

Simple quote from a funny show might prove useful here:
```
Hello IT have you tried turning it off and on again?
```

---

### Post by xaegis on 2009-01-29
ok well I used synaptic to uninstall everything java on my computer then reinstalled. (per your suggestion);)
Apparently Sun JDK, Gij and Open JDK are morally opposed to existing peacefully on the same config.

Problem SOLVED

Thanks!

---

### Post by jespdj on 2009-01-29
> **kavon89 said:**
> Having both the Sun and Open versions of the JDK probably isn't a good idea.
Why not? There's no problem at all with having multiple versions of Java installed at the same time. I have Sun Java 5, 6 and OpenJDK on my system. No problem.
> **xaegis said:**
> Apparently Sun JDK, Gij and Open JDK are morally opposed to existing peacefully on the same config.
No, they aren't. You don't want to use GNU Java (gij) though, it's slow, incompatible and outdated.

---

