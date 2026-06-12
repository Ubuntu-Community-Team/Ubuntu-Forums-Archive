---
title: "Java Path"
date: 2005-11-06
forum: Programming Talk
---

### Post by chadr6 on 2005-11-06
I just installed the Java SDK on Ubuntu 5.10 and I'm looking for a way to permanently set the path variable to include the java bin directory.  I realize that I can do it each time I open the shell by typing PATH=$PATH:/directory, but I want to be able to set it permanently so that each time I open the shell it will just work.  What file do I have to edit and where is it?

---

### Post by LordHunter317 on 2005-11-06
For your user, edit ~/.bashrc.

Globally, edit /etc/profile.

---

### Post by MakubeX on 2005-11-06
In my setup, I had appended the PATH in file bash.bashrc (somewhere in /etc)..

---

### Post by jvictor on 2005-11-07
You need to set in ~/.bashrc and export it

export JAVA_HOME=<blah_blah>
export CLASSPATH=<blah_blah>
export PATH=${JAVA_HOME}/bin:$PATH

---

### Post by ngms27 on 2005-11-07
You don't need to use EXPORT in .bashrc

simply PATH=MyJavaPath:$PATH is enough to make suns Java the default and everything work for that user.

JonnyT

---

