---
title: "Java installing"
date: 2007-07-09
forum: Programming Talk
---

### Post by aliov_85 on 2007-07-09
Hello every body.

I have some problems for installing sdk 6 in my machine.

I downloaded first from sun the file "jdk-6u2-linux-i586.bin" on my desktop, and i moved it into /usr/lib.

then i did this:

>  chmod +x jdk-6u2-linux-i586.bin 

but after when I do either 
1:
> ./jdk-6u2-linux-i586.bin 
I got this message:
> ./jdk-6u2-linux-i586.bin: line 1: syntax error near unexpected token `<'
./jdk-6u2-linux-i586.bin: line 1: `<HTML><HEAD>'

2: or this:
> sudo sh ./jdk-6u2-linux-i586.bin
i got:
> ./jdk-6u2-linux-i586.bin: 1: Syntax error: redirection unexpected

Can some one help me please?

---

### Post by ankursethi on 2007-07-09
Better install from the official repositories. in a terminal, do :
```
sudo apt-get install sun-java6-jdk
```
to install the Java Development Kit.

---

### Post by kknd on 2007-07-09
> **aliov_85 said:**
> 

Can some one help me please?

Strange. I've done this steps  for Java 6, 6u1 and 6u2.

Maybe the file is corrupted?

---

### Post by jespdj on 2007-07-09
> **aliov_85 said:**
> 
I got this message:

 ./jdk-6u2-linux-i586.bin: line 1: syntax error near unexpected token `<'
./jdk-6u2-linux-i586.bin: line 1: `<HTML><HEAD>'

You downloaded it incorrectly.

Go to the [JDK download page](http://java.sun.com/javase/downloads/index.jsp).

Download JDK 6u2. **Do not right-click the link and choose Save As**. This is what you did earlier, and instead of the installation file you saved a HTML page that contains the link. Just click on it, your browser will ask you where to save it.

Anyway, if you do not absolutely need the very latest version of Java (version 6 update 2) then it is better to install it from the Ubuntu repositories:
```
sudo apt-get install sun-java6-jdk
```

Downloading from Sun and running the bin file will not automatically install it in the place that's needed for Ubuntu. You'll need to put it in the right place in the system yourself if you want to do it that way.

---

### Post by growltiger on 2007-07-18
Not to put a too fine a point on it, but the get from Ubuntu of Java 6 does *not* deliver update 2.  And I have been stuffed when trying to use make-jpkg.  Any ideas?

---

### Post by vcardona on 2007-07-19
It sounds like your file is corrupted.  I installed JDK6u2 recently on my system.  I did the following in my home directory.

```

chmod 0755 <java bin file>
./<java bin file>
sudo mv jdk1.6.0_02 /opt
cd /opt
sudo ln -s jdk1.6.0_02 java

```

I then added the following to my .bashrc file.
```

export JAVA_HOME=/opt/java
export PATH=$JAVA_HOME/bin:$PATH

```

The order on $PATH is important.  It allows the system to find Java6 first.  I left Ubuntu's default Java installation alone for now.

---

### Post by growltiger on 2007-07-19
Erm, the point was to avoid having to set classpaths or other environment variables by creating a debian package.  I *know* how to use the shell script.

But I need to have access to a variety of JDKs (1.4.2, 1.5.0, & 1.6.0) and I would prefer to use a package install.

The FCS of Java 6 was easy enough to hack into java-packages.  Not so much with the updates.  I need *this* solution.

---

### Post by growltiger on 2007-07-19
And I  found that if I took rev 31 of java-packages (found here: <https://launchpad.net/ubuntu/gutsy/+source/java-package/0.31>, I could install Java 6u2.

So now I can switch using update-alternatives.  And, speaking for myself, that is a good thing.

(By the way, the version of java-packages available via apt is 28.)

---

