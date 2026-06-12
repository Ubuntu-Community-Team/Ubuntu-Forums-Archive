---
title: "[SOLVED] Java Troubles"
date: 2008-06-23
forum: New to Ubuntu
---

### Post by 133794m3r on 2008-06-23
Yeah... I go to the synaptics package manager... type in JRE and add all of the ones that have JRE in them.... but then when I go to Java's site it says that I don't have it.... can anyone help me w/ this?

---

### Post by evozniak on 2008-06-23
you need these packages
sun-java6-jre
sun-java6-plugin

---

### Post by rockerphil on 2008-06-23
run this in terminal

sudo apt-get install sun-java6-bin sun-java6-jre sun-java6-plugin

that should do the trick

ps. it won't show up on Java's home page, but it works fine

---

### Post by 133794m3r on 2008-06-23
ok... well i have that done... but is there anyway for me to test and make sure that it's working right? I tried the standard test.... since no Java home page (runescape... suckorz I know but works for testing java) and it no worked... but I have those installed... so I have java then? Ok thanks for the help

---

### Post by evozniak on 2008-06-23
check if the problem in java or plugin
type this in terminal java -version

---

### Post by 133794m3r on 2008-06-23
exact message and everything
```
macarthur@macarthur-laptop:~$ java -version
java version "1.6.0_06"
Java(TM) SE Runtime Environment (build 1.6.0_06-b02)
Java HotSpot(TM) Client VM (build 10.0-b22, mixed mode, sharing)
```
so yeah... I hope that that helps

---

### Post by evozniak on 2008-06-23
in firefox type>  **about:plugins**
check for Java(TM) Plug-in 1.6.0_06-b02

---

### Post by 133794m3r on 2008-06-23
I checked and it says that they're all enabled.... well it's up and running now... I don't know why... but it seems to be... thanks for the help thus far.

---

