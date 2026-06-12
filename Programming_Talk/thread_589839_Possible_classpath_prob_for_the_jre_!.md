---
title: "Possible classpath prob for the jre !"
date: 2007-10-24
forum: Programming Talk
---

### Post by Akis on 2007-10-24
I run a 64 bit Ubuntu gutsy and have recently installed "successfully" the jre-6u3-linux-i586.bin.
Unfortunately though I can't use the java command from the terminal, plus when i run a java program i get 
```
exec: 40: java: not found
```
any ideas ?
thanks.

---

### Post by Akis on 2007-10-24
Open Office on the contrary works fine :lolflag:

---

### Post by Ramses de Norre on 2007-10-24
Are the binaries in your path? You can check that with **which java**.
Otherwise you need to either add the directory containing the binaries to your path (in ~/.bashrc) or create symlinks to them in a directory already in your path (like /usr/bin/).

---

### Post by jespdj on 2007-10-24
This is **not** a classpath problem. The classpath is the path that Java uses to find compiled Java class files to load and run. Your problem is that there is no 'java' executable in your path (the PATH is what Ubuntu uses to find native executables to run).

Did you download Java 6 Update 3 from Sun's website and did you try to install it manually? Why don't you install it from the Ubuntu repository?
```
sudo apt-get install sun-java6-jdk
```
Java 6 Update 3 is available in the repository (at least for Gutsy).

---

### Post by Akis on 2007-10-24
> **jespdj said:**
> This is **not** a classpath problem. The classpath is the path that Java uses to find compiled Java class files to load and run. Your problem is that there is no 'java' executable in your path (the PATH is what Ubuntu uses to find native executables to run).

Did you download Java 6 Update 3 from Sun's website and did you try to install it manually? Why don't you install it from the Ubuntu repository?
```
sudo apt-get install sun-java6-jdk
```
Java 6 Update 3 is available in the repository (at least for Gutsy).

OK I should have told you the full story.... at first i had install the icedtea java i tried to install via apt-get the sun's java but I failed... 

So i removed the iced tea java and tried for a second time to install via apt get but it failed again .....

Finally i decided to try [sun's way ]("http://www.java.com/en/download/help/5000010500.xml#selfextracting") but nothing really happens either.

Now Ive tried to install java(JRE1.5) using the install/remove programs and i am getting a new error :lolflag::lolflag:
```
stelios@stelios-laptop:~$ java
The program 'java' can be found in the following packages:
 * cacao
 * j2re1.4
 * kaffe
 * jamvm
 * java-gcj-compat
 * gij-4.1
 * gij-4.2
 * sablevm
```

at first i was getting
```
bash: java command not found
```

If this was windows I am sure it would have to do with that thing that you adjust the system variables:confused: .....

---

