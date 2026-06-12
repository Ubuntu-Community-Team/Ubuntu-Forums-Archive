---
title: "New Be Please Help Setting up Java Env"
date: 2008-08-22
forum: Programming Talk
---

### Post by rmabini on 2008-08-22
Hi guy's especially guru's of linux ubuntu, I would like to get some help, how to install JDK how to used eclipse , setting up maven, subversion server, and others to get started developing

Thanks in advance

---

### Post by LaRoza on 2008-08-22
How to install the JDK is in the sticky. For the rest, I can't help (never did it before). Check the repositories for what you want first (the JDK is in the repos, see sticky)

---

### Post by tinny on 2008-08-22
1. Install all of Sun Java 6 

```

sudo apt-get update
sudo apt-get install sun-java6*

```

Then test if the install worked correctly

```

java -version
javac -version

```

Output should be....

```

:~$ java -version
java version "1.6.0_06"
Java(TM) SE Runtime Environment (build 1.6.0_06-b02)
Java HotSpot(TM) Client VM (build 10.0-b22, mixed mode, sharing)
:~$ javac -version
javac 1.6.0_06

```

2. Download and extract Eclipse. (Eclipse is available in the repositories, but I prefer to download the least version) I just usually extract it into my home folder (but there are other ways).

[http://www.eclipse.org/downloads/](http://www.eclipse.org/downloads/) (download the Java Developers version)

3. setup the JDK within Eclipse

check that Eclipse is using the Sun Java 6 JDK in “Window” > “Preferences” > “Installed JREs”. If its not you will need to “Add” the Sun JDK and set it as the default.

The JDK should be in the "/usr/lib/jvm/" folder.
 
4. Maven is easy

```

sudo apt-get install maven2

```

Or to do it manually visit my blog.
[http://javasoapbox.blogspot.com/2008/04/installing-maven-on-linux.html](http://javasoapbox.blogspot.com/2008/04/installing-maven-on-linux.html)

5. Subversion

[https://help.ubuntu.com/8.04/serverguide/C/subversion.html](https://help.ubuntu.com/8.04/serverguide/C/subversion.html)

If you have problems with subversion post back and ill try and help, ive set it up quite a few times.

---

