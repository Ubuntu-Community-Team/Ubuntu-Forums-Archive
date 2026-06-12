---
title: "Problem compiling Java on 64"
date: 2007-09-25
forum: Programming Talk
---

### Post by Johnny K on 2007-09-25
I'm running 64 bit Ubuntu and am having trouble compiling a Java program that imports java.util.Scanner.

I get the following error:
```
$ javac test.java
----------
1. ERROR in test.java (at line 3)
        import java.util.Scanner;
               ^^^^^^^^^^^^^^^^^
The import java.util.Scanner cannot be resolved
----------
2. ERROR in test.java (at line 9)
        Scanner input = new Scanner( System.in );
        ^^^^^^^
Scanner cannot be resolved to a type
----------
3. ERROR in test.java (at line 9)
        Scanner input = new Scanner( System.in );
                            ^^^^^^^
Scanner cannot be resolved to a type
----------
3 problems (3 errors)
```

I'm aware that people have had this problem before. I tried the suggestions in [this thread]("http://ubuntuforums.org/showthread.php?t=307464") and [this one]("http://www.uluga.ubuntuforums.org/showthread.php?t=546040"), but neither worked. What am I doing wrong?

TIA :)

---

### Post by Johnny K on 2007-09-29
Anyone? I don't mean to bump, but I'm sure there are at least a couple other people who are also having this problem.

---

### Post by dwhitney67 on 2007-09-29
Actually, it might be only you have the problems.  Can you please go thru the steps listed in the first link ('this thread') you provided on how to setup your system to use the "real" java.  I know you said you already followed the steps, but something seems strange because that should have done the trick.

Btw, your program has only one error.  The others that follow are because javac is unable to locate java.util.Scanner.

---

### Post by Johnny K on 2007-09-29
Thanks for the reply. Now that I'm looking at it, it probably has something to do with the fact that I get a bunch of messages that say "jdk alternative does not exist". 

Terminal session:
```
**john@hostname:~$ sudo update-java-alternatives -s java-1.5.0-sun**
Password:
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-1.5.0-sun/bin/appletviewer
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-1.5.0-sun/bin/apt
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-1.5.0-sun/bin/extcheck
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-1.5.0-sun/bin/idlj
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-1.5.0-sun/bin/jarsigner
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-1.5.0-sun/bin/jar
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-1.5.0-sun/bin/javac
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-1.5.0-sun/bin/javadoc
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-1.5.0-sun/bin/javah
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-1.5.0-sun/bin/javap
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-1.5.0-sun/bin/jconsole
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-1.5.0-sun/bin/jdb
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-1.5.0-sun/bin/jinfo
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-1.5.0-sun/bin/jmap
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-1.5.0-sun/bin/jps
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-1.5.0-sun/bin/jsadebugd
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-1.5.0-sun/bin/jstack
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-1.5.0-sun/bin/jstatd
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-1.5.0-sun/bin/jstat
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-1.5.0-sun/bin/native2ascii
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-1.5.0-sun/bin/rmic
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-1.5.0-sun/bin/serialver
Using `/usr/lib/jvm/java-1.5.0-sun/jre/bin/java' to provide `java'.
Using `/usr/lib/jvm/java-1.5.0-sun/jre/bin/keytool' to provide `keytool'.
Using `/usr/lib/jvm/java-1.5.0-sun/jre/bin/orbd' to provide `orbd'.
Using `/usr/lib/jvm/java-1.5.0-sun/jre/bin/pack200' to provide `pack200'.
Using `/usr/lib/jvm/java-1.5.0-sun/jre/bin/policytool' to provide `policytool'.
Using `/usr/lib/jvm/java-1.5.0-sun/jre/bin/rmid' to provide `rmid'.
Using `/usr/lib/jvm/java-1.5.0-sun/jre/bin/rmiregistry' to provide `rmiregistry'.
Using `/usr/lib/jvm/java-1.5.0-sun/jre/bin/servertool' to provide `servertool'.
Using `/usr/lib/jvm/java-1.5.0-sun/jre/bin/tnameserv' to provide `tnameserv'.
Using `/usr/lib/jvm/java-1.5.0-sun/jre/bin/unpack200' to provide `unpack200'.
update-java-alternatives: plugin alternative does not exist: /usr/lib/jvm/java-1.5.0-sun/jre/plugin/amd64/ns7/libjavaplugin_oji.so
update-java-alternatives: plugin alternative does not exist: /usr/lib/jvm/java-1.5.0-sun/jre/plugin/amd64/ns7/libjavaplugin_oji.so
update-java-alternatives: plugin alternative does not exist: /usr/lib/jvm/java-1.5.0-sun/jre/plugin/amd64/ns7/libjavaplugin_oji.so
update-java-alternatives: plugin alternative does not exist: /usr/lib/jvm/java-1.5.0-sun/jre/plugin/amd64/ns7/libjavaplugin_oji.so
[B]john@hostname:~$ sudo -b gedit /etc/jvm
john@hostname:~$ javac WageCalculator.java[/B]
----------
1. ERROR in WageCalculator.java (at line 3)
        import java.util.Scanner;
               ^^^^^^^^^^^^^^^^^
The import java.util.Scanner cannot be resolved
----------
2. ERROR in WageCalculator.java (at line 9)
        Scanner input = new Scanner( System.in );
        ^^^^^^^
Scanner cannot be resolved to a type
----------
3. ERROR in WageCalculator.java (at line 9)
        Scanner input = new Scanner( System.in );
                            ^^^^^^^
Scanner cannot be resolved to a type
----------

```

---

### Post by dwhitney67 on 2007-09-29
I wonder if this has something to do with the fact your on a 64-bit machine?  Have you researched other forums, for instance [linuxquestions.org]("http://www.linuxquestions.org/")?

---

### Post by Johnny K on 2007-09-29
No, I haven't asked there yet. I thought it had something to do with 64, so that's why I thought other people might have the same problem. I guess I'll ask around in the 64 bit section of UF.

But I do have /usr/lib/jvm/ia32-java-1.5.0-sun/jre/bin/java installed, if that means anything.

---

### Post by dwhitney67 on 2007-09-29
Try to determine if your "javac" is pointing to the correct binary.  In other words, start with this:

[FONT="Courier New"]$ which javac[/FONT]

This will tell you where "javac" is referenced.  More than likely it is /usr/bin.  Then run this command, substituting the correct path if necessary, that leads to javac discovered previously.

[FONT="Courier New"]$ ls -l /usr/bin/javac[/FONT]

If that points to something else, then follow it until you determine what binary you are actually calling.  Hopefully it will end up in the JVM directory that you are expecting.  Whether it leads to /usr/lib/jvm/ia32-java-1.5.0-sun/jre/bin might prove interesting.

Btw, my system's javac resides here:  /usr/lib/jvm/java-6-sun-1.6.0.00/jre/bin.  I am on a 32-bit system.

---

### Post by Johnny K on 2007-09-30
Mine leads to /etc/alternatives/javac. Is there anything strange about that?

---

### Post by dwhitney67 on 2007-09-30
No, but you need to "dig deeper"... what does /etc/alternatives/javac point to (and so on)?

---

### Post by Johnny K on 2007-09-30
Oh, sorry about that. I thought javac was a file.

it goes /etc/alternatives/javac -> /usr/bin/ecj

and that's where it stops.

---

### Post by dwhitney67 on 2007-09-30
Tah-dah... it would appear that you are using Canonical's (Ubuntu's) cheesy javac compiler, not the Sun Javac compiler.

Just for grins, in lieu of compiling with the plain-vanilla javac, try compiling like this:

$ /usr/lib/jvm/ia32-java-1.5.0-sun/jre/bin/javac test.java

Normally when you apt-get the java packages, that link from /etc/alternatives is adjusted to point to the Sun javac.  Did you not install Java?

Anyhow, if the test above works, I do not know what else do to.  I would recommend uninstalling Java and then re-installing it again.

Or you could manually set the /etc/alternatives/javac (and other binaries) to point to the correct files by manually setting up the links yourself.

---

### Post by Johnny K on 2007-09-30
Thanks for the great info! I did mess around with Java at some point. I installed and uninstalled a couple of things to try to get a program working.

Anyway, /usr/lib/jvm/ia32-java-1.5.0-sun/jre/bin does not have a file called javac within it. So doing what you said results in this message:
```
bash: /usr/lib/jvm/ia32-java-1.5.0-sun/jre/bin/javac: No such file or directory
```

Did I accidentally remove Sun's Java compiler at some point? When you say I should reinstall Java, which packages are you talking about?

---

### Post by dwhitney67 on 2007-09-30
It looks like you might only have Sun's JRE (Java Runtime Environment).  What you need is the JDK (or SDK, or whatever it's called).  JDK of course is the Java Development Kit.

It really ticks me off that Canonical ships an "inferior" JDK with their product.  I think it would be better to ship the real McCoy or nothing at all.  Naturally some suck-up will disagree with me.

Anyhow, peruse the forums (or use Synaptic Package Manager) to download the real Java Development Kit.  I did it for my system a few weeks and a couple of dozen beers ago, so I can't remember what steps I took, but I do recall it involved using the command line.

---

### Post by Johnny K on 2007-09-30
Thank you!!! You were right, what I needed was the JDK.

For anyone else who might stumble upon this, I was able to get it to work by doing the following in order:
1. Installing *sun-java5-jdk* via synaptic
2. Following the steps provided by hod139 in [this post]("http://ubuntuforums.org/showpost.php?p=1811155&postcount=3")

Thanks again, dwhitney67!

---

### Post by dwhitney67 on 2007-09-30
You're quite welcome.

---

