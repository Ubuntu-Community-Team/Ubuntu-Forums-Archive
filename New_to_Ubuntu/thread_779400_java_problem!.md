---
title: "java problem!"
date: 2008-05-02
forum: New to Ubuntu
---

### Post by tjohannvr on 2008-05-02
I used to be able to use java from the command line, but this function
dissappeared when I upgraded from ubuntu 7.10 to ubuntu 8.04.
I get the output below if I'm trying to access java and compile
a program. 

$ java
The program 'java' can be found in the following packages:
 * java-gcj-compat-headless
 * openjdk-6-jre-headless
 * cacao
 * j2re1.4
 * kaffe
 * jamvm
 * gij-4.1
 * gij-4.2
 * sablevm
Try: sudo apt-get install <selected package>
bash: java: command not found

If anybody can help, please do. This is very erritating.
Thank you.

---

### Post by jamesstansell on 2008-05-04
Try installing the openjdk-6-jre package.

As you can tell, there are a lot of java options, so depending on what you want to do, another package may be better, but openjdk-6-jre is considered the new default for hardy.

---

