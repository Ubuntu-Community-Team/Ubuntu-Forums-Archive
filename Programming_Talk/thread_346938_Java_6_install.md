---
title: "Java 6 install"
date: 2007-01-26
forum: Programming Talk
---

### Post by rkathey on 2007-01-26
Ubuntuers -

I'm switched my Linux flavor from Fedora to Ubuntu and am have a few issues finding packages.  I installed Java 5 which went well using the command

sudo apt-get install sun-java5-jdk

I decided to go ahead and bite the bullet for Java 6 but couldn't find a java 6 package.  Here are the steps I used to install.

[INDENT]download java from [http://java.sun.com/javase/downloads/index.jsp](http://java.sun.com/javase/downloads/index.jsp)
cd to dowload directory
chmod a+x jdk-6-linux-i586.bin
sudo ./jdk-6-linux-i586.bin
sudo mv jdk1.6.0 /usr/lib/jvm/
sudo update-alternatives --install "/usr/bin/java" "java" "/usr/lib/jvm/jdk1.6.0/bin/java" 1
sudo update-alternatives --set java /usr/lib/jvm/jdk1.6.0/bin/java
java -version[/INDENT]

Is the the 'normal' way or is there a package out there I could have installed?

---

### Post by ZylGadis on 2007-01-26
No packages yet (for either Dapper or Edgy), so you did the right thing, I think. The alternative would be to install Feisty three months before its release (and I'm not sure that has jdk6 atm).

---

### Post by phossal on 2007-01-26
I dig your (Sun's) method. That's how I do it, and it's how many of us [recommend]("http://ubuntuforums.org/showthread.php?t=332674") doing it. There *are* packages out there though - all prepared by third parties.

---

### Post by Ramses de Norre on 2007-01-27
Get the bin file from their site, extract it, move it to something like /opt/ and add these to your ~/.bashrc: (with the right path where mine mentions /opt/)```
export JAVA_HOME=/opt/jdk1.6.0
export PATH=${JAVA_HOME}/bin:${PATH}

```

---

### Post by phossal on 2007-01-27
> **Ramses de Norre said:**
> Get the bin file from their site, extract it, move it to something like /opt/ and add these to your ~/.bashrc: (with the right path where mine mentions /opt/)```
export JAVA_HOME=/opt/jdk1.6.0
export PATH=${JAVA_HOME}/bin:${PATH}

```

You can actually do it that^ way to any path. I often leave the Java folder on my desktop. The reason you might move it to /opt, or, /usr/lib, is to included it into your update-alternatives config.

You left that out. ;) You should really include *those* instructions.

---

### Post by Ramses de Norre on 2007-01-27
> **phossal said:**
> You can actually do it that way to any path. I often leave the Java folder on my desktop. The reason you might move it to /opt, or, /usr/lib, is to included it into your update-alternatives config.

You left that out. ;) You should really include *those* instructions.

Or because I don't like directories cluttering my desktop or home folder and being accessible without root privileges. So I move all important executable stuff to /opt/ or /usr/bin/.
And what's the advantage of including it in the update-alternatives path? I've just set the env var and I'll most likely not touch it again until a new java version is released.

---

### Post by phossal on 2007-01-27
> **Ramses de Norre said:**
> Or because I don't like directories cluttering my desktop or home folder and being accessible without root privileges. So I move all important executable stuff to /opt/ or /usr/bin/.
And what's the advantage of including it in the update-alternatives path? I've just set the env var and I'll most likely not touch it again until a new java version is released.

lol Normally, I'm saying the things *you* say. I hardly ever configure update-alternatives. Some users like it though, because they mix techniques for installing Java programs, and some of them rely on there being an active (and current) configuration in alternatives. That's all.

---

### Post by FyreBrand on 2007-01-27
> **rkathey said:**
> Ubuntuers -

I'm switched my Linux flavor from Fedora to Ubuntu and am have a few issues finding packages.  I installed Java 5 which went well using the command

sudo apt-get install sun-java5-jdk

I decided to go ahead and bite the bullet for Java 6 but couldn't find a java 6 package.  Here are the steps I used to install.

[INDENT]download java from [http://java.sun.com/javase/downloads/index.jsp](http://java.sun.com/javase/downloads/index.jsp)
cd to dowload directory
chmod a+x jdk-6-linux-i586.bin
sudo ./jdk-6-linux-i586.bin
sudo mv jdk1.6.0 /usr/lib/jvm/
sudo update-alternatives --install "/usr/bin/java" "java" "/usr/lib/jvm/jdk1.6.0/bin/java" 1
sudo update-alternatives --set java /usr/lib/jvm/jdk1.6.0/bin/java
java -version[/INDENT]

Is the the 'normal' way or is there a package out there I could have installed?Just for future reference sun-java6-<bin, jdk, plugin, source, etc> are in the multiverse repository.  You can enable is with the graphic interface in Synaptic or Adept, or by editing your /etc/apt/sources.list.  Make a backup first.

You can see an example of that in the [Ubuntu Customization Guide]("http://ubuntuforums.org/forumdisplay.php?f=159") in the Third Party Projects section.  There are examples there for Dapper (6.06) and Edgy (6.10).

---

### Post by phossal on 2007-01-27
You're way behind. Most of the developers who play in the forums download Java right from Sun. I was being playful in this thread, but I wrote [a tutorial that sums up Sun's method]("http://ubuntuforums.org/showthread.php?t=332674"). Downloading the packages from the multiverse is okay too, but it isn't necessary. Java isn't an *Ubuntu* program, obviously, so no need to *rely* on Ubuntu to get it. 

Java
eclipse
Tomcat
LimeWire
Open Office

They're just too easy to download. Everything except Java can simply be extracted anywhere you please. Configuring update-alternatives is a snap.

---

### Post by FyreBrand on 2007-01-27
I was just pointing out that it's indeed in the repositories.  Some of us are crazy and like package management.

---

### Post by phossal on 2007-01-27
> **FyreBrand said:**
> Some of us are crazy and like package management.

lol Downloading the .bin file from Sun doesn't prevent the system from managing packages - including Java. ;)

---

### Post by FyreBrand on 2007-01-27
I understand that it doesn't interfere with other package management.  I compile and install a patched wine.  I haven't learned how to let apt manage and update locally installed packages though.  Maybe I'm not understanding what you're saying, but unless I built a deb package from source (maybe with apt-build?) I don't understand how apt is going to track that or integrate it with dependencies.  I find package management not to be a trivial endeavor and I still have a lot to learn.

Since you understand the java install maybe you could read my question in this thread: [http://ubuntuforums.org/showpost.php?p=2072646&postcount=10](http://ubuntuforums.org/showpost.php?p=2072646&postcount=10)

Thanks.

---

### Post by phossal on 2007-01-27
> **FyreBrand said:**
> I don't understand how apt is going to track that or integrate it with dependencies.
I'm not sure I understand what dependencies you're referring to. As for your other question, what do you think *uses* /etc/jvm?

---

### Post by FyreBrand on 2007-01-28
I think that installed applications via package management use /etc/jvm.  Don't they?

---

### Post by phossal on 2007-01-28
> **FyreBrand said:**
> I think that installed applications via package management use /etc/jvm.  Don't they?

Don't they call "java", which is /usr/bin/java, a link managed by update-alternatives?

---

### Post by phossal on 2007-01-28
I'm tired, and I'm being playful, but probably too careless. Eclipse looks for the environment variable JAVA_HOME to run. Eclipse, itself, has a method for determining which compiler is installed, and that search *may* include /etc/jvm. Those setting are also configurable directly from within eclipse.

---

### Post by FyreBrand on 2007-01-28
I answered in the other post and yes I could tell you are prodding me for answers which is okay by me.  If I had the answers I wouldn't have asked the questions so I don't mind trying to figure it out myself either.  At least I will remember looking things up.

I do see your point about something in /etc/jvm, but I've also seen that things are running okay so far without any information about java6 in the file.

---

### Post by upidivl on 2007-02-14
Hello all, I've been horrendous problems getting javac to work.  I kept on getting "bash: javac: command not found"

So, here is what to do (after following the first post):

```

sudo update-alternatives --install "/usr/bin/javac" "javac" "/usr/lib/jvm/jdk1.6.0/bin/javac" 1
sudo update-alternatives --set javac /usr/lib/jvm/jdk1.6.0/bin/javac

```

Yeah, just add 'c' to the correct parts.  :-)

Hopefully that helps somebody!

---

### Post by MadMan2k on 2007-02-14
> **phossal said:**
> You're way behind. Most of the developers who play in the forums download Java right from Sun.
thats a plain lie.

---

### Post by Ramses de Norre on 2007-02-14
I think the repo is way easier than always going to the vendors site, you'll end up with windows like installing methods.
One thing that's handled extremely better by ubuntu in particular and linux in general than by windows are the package managers which deliver a consistent method to install software, I rely on them as much as I can and stay away as much as I can from installing external packages/binaries and/or compiling from source.
But this is a personal decision of course.

---

### Post by phossal on 2007-02-14
> **MadMan2k said:**
> thats a plain lie.
Most people just want to get up and running, and use the the tools they need. While I recommend *your* backports package sometimes, it isn't even an option in many cases. Your package is useful. It isn't *mandatory* or even *easier* than getting java from SUN, though. It certainly isn't an option if you want an older JDK. Your package, by default, poses additional security risks on top of SUN's Java. You don't release updates as fast as they do. And, of course, you can't install it *multiple* times, which is sometimes important. For certain people, downloading the package is a no-brainer, but for me, and plenty others, we wouldn't even consider it.

---

### Post by hobie on 2007-02-27
I installed this and it worked fine. However, I installed Eclipse using Adept and it comes without a JDK.  Trying to run it after the above installation gives:

> A Java Runtime Environment (JRE) or Java Development Kit (JDK)
must be available in order to run Eclipse. No Java virtual machine
was found after searching the following locations:
/usr/lib/j2sdk1.4-sun/bin/java

I tried adding '-vm /etc/alternatives/java' and it almost worked, but crashed in the splash screen.

---

### Post by phossal on 2007-02-27
```
A Java Runtime Environment (JRE) or Java Development Kit (JDK)
must be available in order to run Eclipse. No Java virtual machine
was found after searching the following locations:
**/usr/lib/j2sdk1.4-sun/bin/java**

```

We have to solve the problems one at a time. The first one is this, you haven't run (apparently):
```
sudo update-alternatives --config java
```
When you do, you should select the correct one, and try again. The line in the error message above is explaining that the default Java (1.4) won't run eclipse. If you download JDK6, this is a pretty good indication that the correct Java has not been selected via update-alternatives.

---

### Post by geakMonkey on 2007-02-28
> **FyreBrand said:**
> Some of us are crazy and like package management.

Punny:)

---

