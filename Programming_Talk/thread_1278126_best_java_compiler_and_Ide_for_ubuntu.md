---
title: "best java compiler and Ide for ubuntu"
date: 2009-09-29
forum: Programming Talk
---

### Post by Keevu on 2009-09-29
links and name of best java compiler and ide for ubuntu thanks. :popcorn:

---

### Post by credobyte on 2009-09-29
Sun Java JDK:
```
sudo apt-get install sun-java6-jdk sun-java6-fonts

```

IDE: NetBeans ( [http://www.netbeans.org/](http://www.netbeans.org/) )

---

### Post by NovaAesa on 2009-09-29
either that or try eclipse

---

### Post by Ubu-freak on 2009-09-29
I don't personally like using an IDE. Using vim to write code is much faster.
To compile a file eg foo.java:
```
javac foo.java
```To run foo.class
```
java foo.class
```

---

### Post by chrisjsmith on 2009-09-29
You can write code fast in Vim, but you can't do large refactoring easily, it doesn't understand the context of the language and it doesn't have decent integration with testing tools etc.

Eclipse works well on Ubuntu 9.04 with the standard sun JDK. (sun-java6-jdk)

Don't install eclipse using apt.  Download it from [http://eclipse.org/](http://eclipse.org/) and unpack it in ~/bin/eclipse - it just works.

Netbeans is seriously hyped IMHO and doesn't scale with your project.  Eclipse has decent testing tools and does incremental compilation which saves an insane amount of time waiting for whole-project compliation to run or waiting for entire test suites to run.

---

### Post by Tortel on 2009-09-29
I would also recommend eclipse. Its a very useful program and has many tools.
I believe that Netbeans is better for GUI development in Java, although it creates a complete mess of code.
But you should be familiar with the command line methods of compiling/running Java programs, as mentioned before, just in case you ever need to know them.

---

### Post by chrisjsmith on 2009-09-29
> **Tortel said:**
> But you should be familiar with the command line methods of compiling/running Java programs, as mentioned before, just in case you ever need to know them.

^^ listen to the wise man.  Top tip!

---

### Post by mdmorrison on 2010-07-20
> **Ubu-freak said:**
> I don't personally like using an IDE. Using vim to write code is much faster.
To compile a file eg foo.java:
```
javac foo.java
```To run foo.class
```
java foo.class
```

I've found that gedit included in Ubuntu is pretty good with the highlight modes for various languages.  I've only just started messing around with Eclipse, and was dismayed by the amount of extraneous code (stubs) automatically inserted in the .java file.

---

### Post by navaneethan on 2010-07-20
Shell is very good to learn step by step :-) we can get the completeness of learning .try in shell :-)

---

### Post by ja660k on 2010-07-20
I agree, before using a fancy IDE learn the basics. 
all you really need is gedit/vim/nano (whatever) and the compiler...

eclipse, its better for larger programs containing many classes and design patterns, because things are easier to manage.

netbeans, if your working on web/enterprise systems, i recommend netbeans
it has great support for J2EE and jsp :) also comes with its own tomcat,glassfish server... i guess thats why they call it NETbeans

---

### Post by evstevemd on 2010-07-20
Use Simple editor/IDE and compiler and once you are conversant go for Netbeans/Eclipse/Idea. I prefer geany as lightweight IDE over gedit. You can open terminal right there and compile from commandline

Don't listen to old debate on Netbeans/Eclipse. It is likely to confuse new bees learning to fly :p

---

