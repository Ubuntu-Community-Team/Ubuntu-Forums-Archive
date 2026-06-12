---
title: "frostwire is not working!"
date: 2008-06-06
forum: New to Ubuntu
---

### Post by bob16 on 2008-06-06
i just reinstalled ubuntu with hardy (64bit) and now, i cant run frostwire

heres the message it tells me

Starting FrostWire...
Java exec found in PATH. Verifying...
Suitable java version found [java = 1.6.0_06]
Configuring environment...
Loading FrostWire:
#
# An unexpected error has been detected by Java Runtime Environment:
#
#  SIGSEGV (0xb) at pc=0x00007f951376a755, pid=9701, tid=1085815120
#
# Java VM: Java HotSpot(TM) 64-Bit Server VM (10.0-b22 mixed mode linux-amd64)
# Problematic frame:
# C  [libc.so.6+0x30755]  catgets+0x15
#
# An error report file with more information is saved as:
# /usr/lib/frostwire/hs_err_pid9701.log
#
# If you would like to submit a bug report, please visit:
#   [http://java.sun.com/webapps/bugreport/crash.jsp](http://java.sun.com/webapps/bugreport/crash.jsp)
# The crash happened outside the Java Virtual Machine in native code.
# See problematic frame for where to report the bug.
#
/usr/lib/frostwire/runFrostwire.sh: line 125:  9701 Aborted                 ${JAVA_PROGRAM_DIR}java -ea -Dorg.apache.commons.logging.Log=org.apache.commons.logging.impl.NoOpLog -Djava.library.path=. $EXECUTABLE -jar FrostWire.jar $ARGUMENTS


******************************************************************
Something went wrong with FrostWire.
Maybe you're using the wrong version of Java?
(FrostWire is tested against and works best with with Sun's JRE, Java 1.4+)
The version of Java in your PATH is:
java version "1.6.0_06"
Java(TM) SE Runtime Environment (build 1.6.0_06-b02)
Java HotSpot(TM) 64-Bit Server VM (build 10.0-b22, mixed mode)


i installed java usind the restricted extras in terminal and i also installed another java from synaptics (its like java jre6 or something)

i rly dont know what i should do now. i also tried this in terminal

 sudo update-java-alternatives -s java-6-sun

and that always fixed my problems when i had some with frostwire/java.

---

### Post by SunnyRabbiera on 2008-06-07
Java implementation in a 64 bit environment is still not quite there yet, but it will be soon thanks to java opening the source code to us.
Do you have open office working though?

---

### Post by bob16 on 2008-06-07
> **SunnyRabbiera said:**
> Java implementation in a 64 bit environment is still not quite there yet, but it will be soon thanks to java opening the source code to us.
Do you have open office working though?
yes, open office works perfectly.

before, when i used gusty 64bit, frostwire worked perfectly so java is not the proble (i think)

---

### Post by Zer0Nin3r on 2008-06-07
I'm not running 64-Bit, but when I emailed the Frostwire team about a different error that I'm having they gave me a link as well.

> If your Ubuntu 8.04 is running on an AMD 64bit kernel, I recommend you follow this instructions: [http://frostwire.wordpress.com/2008/06/01/problems-running-frostwire-on-ubuntu-804-with-64bit-jvm/]("http://frostwire.wordpress.com/2008/06/01/problems-running-frostwire-on-ubuntu-804-with-64bit-jvm/")


The problem that I am having has to do with the OpenJDK environment.  I already have the recommended Java environments recommended by the Frostwire team installed, I just don't know how to interface/associate the two together.

```
Starting FrostWire...

Java exec found in PATH. Verifying...

Suitable java version found [java = 1.6.0]

Configuring environment...

Loading FrostWire:

java.lang.UnsatisfiedLinkError: Can\'t load library: /usr/lib/jvm/java-6-openjdk/jre/lib/i386/motif21/libmawt.so

       at java.lang.ClassLoader.loadLibrary(ClassLoader.java:1666)

       at java.lang.Runtime.load0(Runtime.java:787)

       at java.lang.System.load(System.java:1022)

       at java.lang.ClassLoader$NativeLibrary.load(Native Method)

       at java.lang.ClassLoader.loadLibrary0(ClassLoader.java:1767)

       at java.lang.ClassLoader.loadLibrary(ClassLoader.java:1684)

       at java.lang.Runtime.loadLibrary0(Runtime.java:840)

       at java.lang.System.loadLibrary(System.java:1047)

       at sun.security.action.LoadLibraryAction.run(LoadLibraryAction.java:67)

       at sun.security.action.LoadLibraryAction.run(LoadLibraryAction.java:47)

       at java.security.AccessController.doPrivileged(Native Method)

       at java.awt.Toolkit.loadLibraries(Toolkit.java:1610)

       at java.awt.Toolkit.<clinit>(Toolkit.java:1632)

       at com.limegroup.gnutella.gui.Main.showInitialSplash(Main.java:67)

       at com.limegroup.gnutella.gui.Main.main(Main.java:39)





******************************************************************

Something went wrong with FrostWire.

Maybe you\'re using the wrong version of Java?

(FrostWire is tested against and works best with with Sun\'s JRE, Java 1.4+)

The version of Java in your PATH is:

java version \"1.6.0\"

OpenJDK Runtime Environment (build 1.6.0-b09)

OpenJDK Server VM (build 1.6.0-b09, mixed mode)

```

**Update**
Solved the problem with help from this [thread]("http://ubuntuforums.org/showthread.php?t=779386&highlight=frostwire") by running the command:

```
sudo update-java-alternatives -s java-6-sun 
```

Another helpful spot is the [Wiki page]("https://help.ubuntu.com/community/FrostWire") on Frostwire

---

### Post by bob16 on 2008-06-08
> **Zer0Nin3r said:**
> I'm not running 64-Bit, but when I emailed the Frostwire team about a different error that I'm having they gave me a link as well.



The problem that I am having has to do with the OpenJDK environment.  I already have the recommended Java environments recommended by the Frostwire team installed, I just don't know how to interface/associate the two together.

```
Starting FrostWire...

Java exec found in PATH. Verifying...

Suitable java version found [java = 1.6.0]

Configuring environment...

Loading FrostWire:

java.lang.UnsatisfiedLinkError: Can\'t load library: /usr/lib/jvm/java-6-openjdk/jre/lib/i386/motif21/libmawt.so

       at java.lang.ClassLoader.loadLibrary(ClassLoader.java:1666)

       at java.lang.Runtime.load0(Runtime.java:787)

       at java.lang.System.load(System.java:1022)

       at java.lang.ClassLoader$NativeLibrary.load(Native Method)

       at java.lang.ClassLoader.loadLibrary0(ClassLoader.java:1767)

       at java.lang.ClassLoader.loadLibrary(ClassLoader.java:1684)

       at java.lang.Runtime.loadLibrary0(Runtime.java:840)

       at java.lang.System.loadLibrary(System.java:1047)

       at sun.security.action.LoadLibraryAction.run(LoadLibraryAction.java:67)

       at sun.security.action.LoadLibraryAction.run(LoadLibraryAction.java:47)

       at java.security.AccessController.doPrivileged(Native Method)

       at java.awt.Toolkit.loadLibraries(Toolkit.java:1610)

       at java.awt.Toolkit.<clinit>(Toolkit.java:1632)

       at com.limegroup.gnutella.gui.Main.showInitialSplash(Main.java:67)

       at com.limegroup.gnutella.gui.Main.main(Main.java:39)





******************************************************************

Something went wrong with FrostWire.

Maybe you\'re using the wrong version of Java?

(FrostWire is tested against and works best with with Sun\'s JRE, Java 1.4+)

The version of Java in your PATH is:

java version \"1.6.0\"

OpenJDK Runtime Environment (build 1.6.0-b09)

OpenJDK Server VM (build 1.6.0-b09, mixed mode)

```

**Update**
Solved the problem with help from this [thread]("http://ubuntuforums.org/showthread.php?t=779386&highlight=frostwire") by running the command:

```
sudo update-java-alternatives -s java-6-sun 
```

Another helpful spot is the [Wiki page]("https://help.ubuntu.com/community/FrostWire") on Frostwire
about the sudo update-java-alternatives -s java-6-sun

i tried it

that always fixed my problems when i was using gusty 64bit

so i this is a different problem

---

### Post by robertchahine on 2008-06-08
write this in the console
```

sudo update-alternatives --config java
```
and there will be 2 options.
choose the seconde option (not in use)

---

### Post by Zer0Nin3r on 2008-06-09
> **bob16 said:**
> about the sudo update-java-alternatives -s java-6-sun

i tried it

that always fixed my problems when i was using gusty 64bit

so i this is a different problem

I understand, but have you tried visiting this link?

[http://frostwire.wordpress.com/2008/06/01/problems-running-frostwire-on-ubuntu-804-with-64bit-jvm/]("http://frostwire.wordpress.com/2008/06/01/problems-running-frostwire-on-ubuntu-804-with-64bit-jvm/")

---

### Post by rockerphil on 2008-06-09
it seems to me that all the java problems i see have to do with Open JDK. have you tried using the non open source Java? it may solve your progblem

---

### Post by bob16 on 2008-06-10
> **rockerphil said:**
> it seems to me that all the java problems i see have to do with Open JDK. have you tried using the non open source Java? it may solve your progblem
where can i get that version?

---

### Post by bob16 on 2008-06-17
i think frostwire was the problem.
i installed limewire and it works perfect

---

