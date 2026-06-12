---
title: "can not find JVM"
date: 2008-10-18
forum: Programming Talk
---

### Post by hakimade on 2008-10-18
hello can any body tell me how to go about this

{code}

hakimade@Hakimade-WorkShop:~$ javac
The program 'javac' can be found in the following packages:
 
* java-gcj-compat-dev
 * jikes-sablevm (You will have to enable component called 'universe')
 
* gcj-4.2
 * kaffe (You will have to enable component called 'universe')
 
* ecj

* jikes-sun (You will have to enable component called 'multiverse')
 
* j2sdk1.4 (You will have to enable component called 'multiverse')
 
* jikes-classpath (You will have to enable component called 'universe')
 
* jikes-gij (You will have to enable component called 'universe')
 
* gcj-4.1 (You will have to enable component called 'universe')

* sun-java5-jdk (You will have to enable component called 'multiverse')
 
* jikes-kaffe (You will have to enable component called 'universe')
 
* sun-java6-jdk (You will have to enable component called 'multiverse')
Try: sudo apt-get install <selected package>
bash: javac: command not found

{code}

hakimade@Hakimade-WorkShop:~$

---

### Post by pdwerryhouse on 2008-10-18
You probably want Sun's JDK. As it says, you will have to make sure the multiverse components are in apt's /etc/apt/sources.list file, so check for something like this and add it if it isn't there:

```

deb http://us.archive.ubuntu.com/ubuntu/ hardy multiverse

```

Then:

```

sudo apt-get update
sudo apt-get install sun-java6-jdk

```

---

### Post by snova on 2008-10-18
It means you don't have Java installed (or development tools, anyway). But Java has been reimplemented many times, and these are all the options you have.

I can't compare them since I just stuck with the first one that ran Eclipse correctly (which sadly wasn't the GNU one).

---

### Post by drubin on 2008-10-19
Take a look at my sig for installing java.

---

