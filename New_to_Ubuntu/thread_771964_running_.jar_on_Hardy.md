---
title: "running .jar on Hardy"
date: 2008-04-28
forum: New to Ubuntu
---

### Post by basilwatson on 2008-04-28
Hi all
Just tried to run a .jar file on hardy and its not being recognised , have installed Java , but to no avail 

Whats the story with Java under hardy heron ??? 

Stephen

---

### Post by hyper_ch on 2008-04-28
are you sure you have installed java?

For me .jars run just fine.

---

### Post by kpkeerthi on 2008-04-28
What happens when you run the below commands? Post the output here.
```
java -version
```
```
java -jar /path/to/file.jar
```

---

### Post by basilwatson on 2008-04-28
I think so , I downloaded it from sun then , installed ,,, but maybe not Ill recheck

Stephen

---

### Post by basilwatson on 2008-04-28
> **kpkeerthi said:**
> What happens when you run the below commands? Post the output here.
```
java -version
```
```
java -jar /path/to/file.jar
```
s@s-desktop:~$ java -version
java version "1.6.0"
OpenJDK Runtime Environment (build 1.6.0-b09)
OpenJDK Client VM (build 1.6.0-b09, mixed mode, sharing)
s@s-desktop:~$ java -jar /path/to/file.jar
Unable to access jarfile /path/to/file.jar
s@s-desktop:~$ 

this is the output of those codes

and when i add the file path to java ja /home/s/xyz

the program runs , ( before i would right mouse click , open with ,,,) 

? 
is there a short cut for this?

Stephen 

Stephen

---

### Post by kpkeerthi on 2008-04-28
Replace /path/to/file.jar to the actual path to the jar file your are trying to run in ```
java -jar /path/to/file.jar
```

---

### Post by hyper_ch on 2008-04-28
> **basilwatson said:**
> I think so , I downloaded it from sun then , installed ,,, but maybe not Ill recheck

Stephen

You do not download and install software from websites and stuff... you should use the package manager to do so.

---

