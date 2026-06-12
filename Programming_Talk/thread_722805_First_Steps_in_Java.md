---
title: "First Steps in Java"
date: 2008-03-12
forum: Programming Talk
---

### Post by Stochastics on 2008-03-12
Hi everyone,

I want to start programming in Java with Ubuntu 7.10 but i have absolutely no idea what i need to install to be up and running. I don't even know the difference between JSE and JEE...so if anyone of you can explain me what to do, i will be very happy ! Oh, i want to use the netbeans IDE from SUN. 

Thanks !

Stochastics

---

### Post by nick_h on 2008-03-12
> Oh, i want to use the netbeans IDE from SUN.
Start by installing the netbeans package from the repositories (multiverse) - [link](http://packages.ubuntu.com/search?keywords=netbeans&searchon=names&suite=gutsy&section=all).
```
sudo apt-get update
sudo apt-get install netbeans5.5
```

---

### Post by LaRoza on 2008-03-12
See the sticky. It has a link to getting set up with Java.

---

### Post by themusicwave on 2008-03-12
Well for starters, there are three main Java APIs They are:

Java Standard Edition(SE) - desktop applications
Java Enterprise Edition(EE) - enterprise and web applications
Java Micro Edition(ME) - Embedded applications, like cell phones

You'll most likely want Java SE to build desktop applications.

Also there are two important parts of Java, the JDK and the JRE.

The Java Development Kit(JDK) is what developers use to build applications.  It has the javac jacacompiler and other tools.

The Java Runtime Eviroment(JRE) is what you need to run Java applications.

You need to install teh most recent version, version 6 of each of them:
> 
sudo apt-get install sun-java6-bin sun-java6-jdk sun-java6-jre sun-java6-plugin


Check the version with:
> 
java -version


Mine Says:
> 
jon@jon-laptop-ubuntu:~$ java -version
java version "1.6.0_03"
Java(TM) SE Runtime Environment (build 1.6.0_03-b05)
Java HotSpot(TM) Server VM (build 1.6.0_03-b05, mixed mode)
jon@jon-laptop-ubuntu:~$ 


You now have all the tools.

No go to [http://www.netbeans.org]("http://www.netbeans.org") and download netbeans 6, the one in the repos is 5.5.

After that you'll need som tutorials check out:

[http://www.javaranch.com]("http://www.javaranch.com") particularly the cattle drives.

You should be good to go from there.

---

### Post by Stochastics on 2008-03-12
Thanks !

---

### Post by themusicwave on 2008-03-12
I also forgot one thing.

The Java SE API is located here, it has a list of all the libraries that make up Java SE.  There are a lot of them!

[http://java.sun.com/javase/6/docs/api/]("http://java.sun.com/javase/6/docs/api/")

---

### Post by Stochastics on 2008-03-12
I've done the steps for the installation of Java, but, when i open the command line interface and write

steeve@steeve-laptop:~$ java -version
java version "1.4.2-02"
Java(TM) 2 Runtime Environment, Standard Edition (build Blackdown-1.4.2-02)
Java HotSpot(TM) Client VM (build Blackdown-1.4.2-02, mixed mode)

not the same version as you....what's going on here ?

Stochastics

---

### Post by themusicwave on 2008-03-12
Did you install the packages ending in 6?

It appears you have JDK 1.4 installed, this is 2 versions behind the current one.

Did you paste my command as it is shown.  Also, you may need to enable the universe and multiverse sources.

---

### Post by Stochastics on 2008-03-12
Yes, I've done that, and in the synaptic manager, when i go to the installed programs, it shows sun-java6-bin, sun-java6-jdk, sun-java6-jre and sun-java6-plugin...any idea ?

---

### Post by Stochastics on 2008-03-12
Check this...

steeve@steeve-laptop:~$ sudo apt-get install sun-java6-bin sun-java6-jdk sun-java6-jre sun-java6-plugin
[sudo] password for steeve:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
sun-java6-bin is already the newest version.
sun-java6-jdk is already the newest version.
sun-java6-jre is already the newest version.
sun-java6-jre set to manual installed.
sun-java6-plugin is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

strange huh ?

---

### Post by lnostdal on 2008-03-12
you can have multiple versions of one "software-type" installed at the same time .. try

```

sudo update-alternatives --config java

```

..then make sure you select Suns version of Java .. (*/usr/lib/jvm/java-6-sun/jre/bin/java* is what it looks like on my machine)

after doing that try *java -version* again

---

### Post by Stochastics on 2008-03-12
Wow, you are my hero ! :)
Thanks, it worked ! Now, i have the latest programs ;).

Stochastics.

---

### Post by themusicwave on 2008-03-12
> **lnostdal said:**
> you can have multiple versions of one "software-type" installed at the same time .. try

```

sudo update-alternatives --config java

```

..then make sure you select Suns version of Java .. (*/usr/lib/jvm/java-6-sun/jre/bin/java* is what it looks like on my machine)

after doing that try *java -version* again


Thanks, I totally forgot about that command.  I'm sure this will solve your issues.

You can have multiple java versions installed, this is because some applications target a specific JRE.

---

### Post by jcobban on 2008-03-13
[QUOTE=themusicwave;4504794]

You need to install teh most recent version, version 6 of each of them:


When I issue the quoted command eventually the Sun license agreement is displayed.  I have to demonstrate my agreement to the license requirements.  How do I do that? Nothing I typed would cause the window to close and the installation to continue.

---

### Post by themusicwave on 2008-03-13
It has honestly been awhile since I installed Java.  Is there a GUI or just command line?

Maybe try typing y <enter>

---

### Post by LaRoza on 2008-03-14
> **jcobban said:**
> [QUOTE=themusicwave;4504794]

You need to install teh most recent version, version 6 of each of them:


When I issue the quoted command eventually the Sun license agreement is displayed.  I have to demonstrate my agreement to the license requirements.  How do I do that? Nothing I typed would cause the window to close and the installation to continue.

<tab> to get to the "button"

---

