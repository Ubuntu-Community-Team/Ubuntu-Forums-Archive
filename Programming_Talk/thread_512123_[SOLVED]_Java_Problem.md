---
title: "[SOLVED] Java Problem"
date: 2007-07-28
forum: Programming Talk
---

### Post by bskafh on 2007-07-28
Hi, I am a new Ubuntu user and I am having a problem installing the java run time environment.
I installed JRE 1.4.2 and it was working fine until I tried to upgrade it to the new version. I had some problems, so i reinstalled JRE 1.4.2 to try and repeat the whole thing and I keep getting this when I run "java -version"

bilo@bilo-laptop:~/Desktop$ java -version
The program 'java' can be found in the following packages:
* j2re1.4
* gij-4.1
* kaffe
* jamvm
* java-gcj-compat
* cacao
* sablevm
Try: sudo apt-get install <selected package>
Make sure you have the 'universe' component enabled
bash: java: command not found


any help? thank you

---

### Post by samjh on 2007-07-28
How did you install Java?

The recommended method is to use apt-get or Synaptic, like this:
```
sudo apt-get install sun-java6-jre
```

---

### Post by phossal on 2007-07-28
[This thread on installing Java]("http://ubuntuforums.org/showthread.php?t=332674") has 20 *thousand* views - it's the one I use when I install Java(s).

---

### Post by bskafh on 2007-07-29
Thanks a lot its working fine now

---

