---
title: "Installing java compiler"
date: 2007-05-08
forum: Programming Talk
---

### Post by lrhaugen on 2007-05-08
Hi all!

I am pretty new with linux, and I am trying to install the java compiler.

I have installed java6 (apt-get install sun-java6-jdk), and everything works fine with Eclipse.
But I want to compile my class in a terminal, using javac. when typing javac myclass.java I get this:

The program 'javac' can be found in the following packages:
*....

I searched the forum, found and tried this:
([http://ubuntuforums.org/showthread.php?t=333162](http://ubuntuforums.org/showthread.php?t=333162))
export JAVA_HOME='usr/lib/jvm/java-6-sun'
PATH=.:$JAVA_HOME/bin:$JAVA_HOME/jre/bin:$PATH 

to the 
/home/<myuser>/.bashrc

the result is the same, javac cannot be found.

Can you please help me with this?

Thanks!

---

### Post by phossal on 2007-05-08
The thread you used to adjust your path is somewhat out of date. My signature contains the tutorial that I (and a few thousand other people) use to install Java.

[EDIT] Consider this: let's say the backports package of Java (the one you installed) contains Javac. Let's say you just installed it, and then you just edited your .bashrc. If you don't open a new prompt, or you don't issue the command: *source ~/.bashrc*, your computer wouldn't realize that you had edited your .bashrc. That could be a simple problem. However, I recommend using the link in my signature to install javac into update-alternatives.

---

### Post by lrhaugen on 2007-05-08
:-) thanks!

---

