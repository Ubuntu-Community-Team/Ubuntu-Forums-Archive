---
title: "[SOLVED] So i managed to update java..."
date: 2007-11-07
forum: Programming Talk
---

### Post by uberubert on 2007-11-07
Hi!
I managed to find (after an hour or so of searching the net) out that I need to type in "update-java-something something" to make my newly installed java 6 be used instead of the built in 1.4 thing.
(After spending another hour trying to figure out how to install java 6 at all)
Typing "java -version" resulted in seeing that version 6 is now in use.

However, when compiling with javac, i get an error on some hashmapcode stating that "source needs to be 5.0"...
Hey what? didn't I just install and "enable" the use of version 6? I've searched some more, but I cannot find an answer... *tired and weary*

Thanks for anything helpful :)

---

### Post by NeoLithium on 2007-11-07
Check out [http://www.ubuntuguide.org](http://www.ubuntuguide.org)  If you enable the additional repositories you should be able to install java 6 with the add/remove, apt, or synaptic :)

---

### Post by tenmillionmilesaway on 2007-11-07
I expect that the command you did was ```
sudo update-alternatives --config java
```
Even though it kind of looks like you updated Java to 1.6 you actually only updated the java command, ie the one for running compiled Java classes.  You also need to update javac, the java compiler.  Do this by ```
sudo update-alternatives --config javac
```

Depending on your needs you may also need to update javadoc, javah, or any of the other java commands.

Richard

---

### Post by uberubert on 2007-11-08
Hah! That was great! Now javac has been updated as well. Thank you!

---

