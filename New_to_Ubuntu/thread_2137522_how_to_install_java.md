---
title: "how to install java ?"
date: 2013-04-21
forum: New to Ubuntu
---

### Post by nelsua on 2013-04-21
how to install java?

---

### Post by speartip on 2013-04-21
2 choices.
You can either install openjdk version 6 or 7 from the repo.
Or you can install the official Oracle version, instructions here:
[http://www.webupd8.org/2012/01/install-oracle-java-jdk-7-in-ubuntu-via.html](http://www.webupd8.org/2012/01/install-oracle-java-jdk-7-in-ubuntu-via.html)

Hope this helps.

---

### Post by hendrel on 2013-04-22
Here is a blog with step by step instructions on installing Java. [http://hendrelouw73.wordpress.com/2013/04/16/how-to-install-oracle-java-7-update-21-on-ubuntu-12-10-linux/](http://hendrelouw73.wordpress.com/2013/04/16/how-to-install-oracle-java-7-update-21-on-ubuntu-12-10-linux/)

---

### Post by speartip on 2013-04-22
Excellent guide Hendrel.
However for a newbie, it's far easier to use the webupd8 ppa.
It's simply a case of copying & posting 3 commands in a terminal.

---

### Post by slickymaster on 2013-04-22
> **speartip said:**
> ...
However for a newbie, it's far easier to use the webupd8 ppa.
It's simply a case of copying & posting 3 commands in a terminal.

Completely right.

And here they are:
```
sudo add-apt-repository ppa:webupd8team/java
sudo apt-get update
sudo apt-get install oracle-java7-installer
```

---

### Post by hendrel on 2013-04-22
I am aware of ppa's, however the individual installation steps are not transparent to the end user. Step by step instructions can still be followed by a newbie and carry far more educational content.

---

### Post by Cheesemill on 2013-04-22
> **hendrel said:**
> I am aware of ppa's, however the individual installation steps are not transparent to the end user. Step by step instructions can still be followed by a newbie and carry far more educational content.

This is true, however, using the manual installation method means that the user has to manually check for and install security updates.

For something like Java which is well known for having serious vulnerabilities discovered on a regular basis I would definitely recommend going the PPA route so that Java is automatically updated every time there is a new release.

---

### Post by AndyOpie150 on 2013-04-22
+1 ^

---

### Post by craig10x on 2013-04-22
Highly recommend you download the web8 ppa (by doing the 3 terminal commands they show) not only does it install Oracle Java but it adds an updater to your software sources and you'll always get the latest java update through ubuntu's software updater...I use it and it is excellent...

---

### Post by ArminasAnarchy on 2013-04-22
I find the duinsoft script works really well for me - though there's a little more messing about getting it working (you can't just add the ppa).

If you google "java ubuntu" there's an Ubuntu wiki-page that comes up? That's pretty comprehensive.

---

### Post by QIII on 2013-04-22
> **ArminasAnarchy said:**
> I find the duinsoft script works really well for me - though there's a little more messing about getting it working (you can't just add the ppa).

If you google "java ubuntu" there's an Ubuntu wiki-page that comes up? That's pretty comprehensive.

There is a link to the wiki in my signature.  I put the webupd8 method at the top of the command line methods because it is simply the easiest method and the most quickly updated.

---

