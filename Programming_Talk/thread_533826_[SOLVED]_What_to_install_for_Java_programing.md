---
title: "[SOLVED] What to install for Java programing"
date: 2007-08-24
forum: Programming Talk
---

### Post by ubuntu27 on 2007-08-24
Hello folks. 

I helped a friend last night to install Ubuntu. 
I helped him a lot with many things. 
But now I am facing with something I don't know. He is a programmer, a Java programmer to be precise.

What programs does he needs to be able to program?  Also, Is there a difference programming Java in Ubuntu Linux than programming Java in Windows?

---

### Post by Ramses de Norre on 2007-08-24
He'll need the jdk, which can be downloaded from the repo or directly from sun (there are very straight-forward install instructions).
The programming isn't different except maybe his IDE or editor, if he used one like eclipse or netbeans even that wont be necessary ;)
I guess he's just a starting java programmer if he doesn't know these things himself? Java isn't OS dependent, as long as you can get a JRE it'll work.

---

### Post by ubuntu27 on 2007-08-24
I am the the one who dosn't know aout any programming at all ><

He is in the university like me, only different career (I am in Business). He wants to be a programmer or something, System Engineer. Right now he almost finished learning Java, now for the next term he is going to learn C (or was it C++ ?)

Ok, so I noticed I wanted to know about IDEs or Editors. What are the options?

---

### Post by slamdunk12 on 2007-08-24
hi there ubuntu27,

The first thing you need to do is to download the Java Development Kit (JDK) which is available through Synaptic package manager, you need to ask your friend which JDK he uses for his previous operating system. Some java programmers are very particular about this :) Search the JDK through Synaptic and ask your programmer friend which package he needs. Synaptic won't automatically select certain packages like Java Documentation or the necessary JDK font so select accordingly.

Once the JDK is install through Synaptic package manager, execute the following line through Terminal:

```
sudo update-alternatives --config java
```

It will show you several flavor of Java, select the one you just installed.

Then follow by:

```
sudo update-alternatives --config javac
```

It will show you several flovor of Javac, select the one you just installed.

Then follow by:

```
sudo update-alternatives --config jre
```

Again, pick the one you just installed. Java and JRE is the terminal code to execute a compiled java program, javac is used to compile java source code so proper configuration is very important for a java programmer.

By the way, if he ask for Netbeans or Eclipse, just install it through Synaptic and it is good to go. The rule of thumb is to compile and run the java program through terminal first before attempting to compile using IDE.

Cheers!

---

### Post by apetresc on 2007-08-24
EDIT: Arrg, slamdunk posted while I was typing. Disregard this, I suppose, since his instructions are more detailed than mine :)

To be more specific, all your friend needs to do is make sure the multiverse repository is enabled, and then type ```
sudo apt-get install sun-java6-jdk
``` and Ubuntu will install everything he needs to compile and run Java applications.

If he'd like a very powerful Java IDE, he can do ```
sudo apt-get install netbeans5.5
```

---

### Post by slamdunk12 on 2007-08-24
> EDIT: Arrg, slamdunk posted while I was typing.

AdrianP, Sorry mate :lolflag:

---

### Post by tszanon on 2007-08-24
I prefer to get the JDK from Sun ([http://java.sun.com](http://java.sun.com)) and use Eclipse as the DE. Just remember to create a symlink in /usr/local/bin for the java executable (jdk_dir/bin/java).

---

### Post by hod139 on 2007-08-24
> **slamdunk12 said:**
> 
Once the JDK is install through Synaptic package manager, execute the following line through Terminal:

```
sudo update-alternatives --config java
```It will show you several flavor of Java, select the one you just installed.

You should not use update-alternatives for java, instead use 
```
update-java-alternatives
``` See my howto for how to install java and eclipse: [http://ubuntuforums.org/showthread.php?t=201378](http://ubuntuforums.org/showthread.php?t=201378)

The reason not to use "update-alternatives" is that it won't set all the java related settings, only the ones you select.  update-java-settings will update all to use the same version.

---

### Post by CptPicard on 2007-08-24
Why does someone who is in Systems Engineering need help from a Business major in helping set up his Linux box for Java programming? :confused:

---

### Post by ubuntu27 on 2007-08-24
Thank you everyone. I apreciate your imputs. :)

> **CptPicard said:**
> Why does someone who is in Systems Engineering need help from a Business major in helping set up his Linux box for Java programming? :confused:

haha. Becuase I am a "geeker" than him? :P  ><

---

