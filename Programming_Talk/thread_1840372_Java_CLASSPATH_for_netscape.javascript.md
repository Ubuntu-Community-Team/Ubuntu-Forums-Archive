---
title: "Java CLASSPATH for netscape.javascript"
date: 2011-09-07
forum: Programming Talk
---

### Post by jpr0 on 2011-09-07
Hi, 

I've been looking round and found quite a few posts related to the issue I'm having (so I apologize if this is ntuplate thread), but I have no idea how I'm supposed to resolve the problem. 

I have a java file I'm trying to compile: 

```
$ cat fileopen.java 
import java.io.*;
import java.awt.*;
import java.awt.event.*;
import javax.swing.*;
import javax.swing.filechooser.*;
import java.applet.Applet;
import java.awt.Graphics;
import netscape.javascript.*;
...
```

When I try compiling I get the following error: 

```
$ javac fileopen.java 
fileopen.java:8: package netscape.javascript does not exist
import netscape.javascript.*;
^
```

Apparently I somehow have to include some library somewhere on my machine that contains the netscape.javascript class, and this can be done by setting the CLASSPATH environment variable. I read that this is in the file "plugin.jar". The only file I find with that name is here: 

```
$ locate plugin.jar
/usr/share/icedtea-web/plugin.jar
```

Is this the correct jar file? Apparently my machine is using openjdk:

```
$ which java
/usr/bin/java
$ ls -l /usr/bin/java
lrwxrwxrwx 1 root root 22 2011-08-01 16:04 /usr/bin/java -> /etc/alternatives/java
$ ls -l /etc/alternatives/java
lrwxrwxrwx 1 root root 40 2011-08-01 16:04 /etc/alternatives/java -> /usr/lib/jvm/java-6-openjdk/jre/bin/java 
$ java -version
java version "1.6.0_22"
OpenJDK Runtime Environment (IcedTea6 1.10.2) (6b22-1.10.2-0ubuntu1~11.04.1)
OpenJDK 64-Bit Server VM (build 20.0-b11, mixed mode)
``` 

The CLASSPATH environment variable is blank. Does anyone know how I'm supposed to set this up so my program will compile? 
Thanks in advance.

---

### Post by ofnuts on 2011-09-07
> **jpr0 said:**
> Hi, 

I've been looking round and found quite a few posts related to the issue I'm having (so I apologize if this is ntuplate thread), but I have no idea how I'm supposed to resolve the problem. 

I have a java file I'm trying to compile: 

```
$ cat fileopen.java 
import java.io.*;
import java.awt.*;
import java.awt.event.*;
import javax.swing.*;
import javax.swing.filechooser.*;
import java.applet.Applet;
import java.awt.Graphics;
import netscape.javascript.*;
...
```When I try compiling I get the following error: 

```
$ javac fileopen.java 
fileopen.java:8: package netscape.javascript does not exist
import netscape.javascript.*;
^
```Apparently I somehow have to include some library somewhere on my machine that contains the netscape.javascript class, and this can be done by setting the CLASSPATH environment variable. I read that this is in the file "plugin.jar". The only file I find with that name is here: 

```
$ locate plugin.jar
/usr/share/icedtea-web/plugin.jar
```Is this the correct jar file? Apparently my machine is using openjdk:

```
$ which java
/usr/bin/java
$ ls -l /usr/bin/java
lrwxrwxrwx 1 root root 22 2011-08-01 16:04 /usr/bin/java -> /etc/alternatives/java
$ ls -l /etc/alternatives/java
lrwxrwxrwx 1 root root 40 2011-08-01 16:04 /etc/alternatives/java -> /usr/lib/jvm/java-6-openjdk/jre/bin/java 
$ java -version
java version "1.6.0_22"
OpenJDK Runtime Environment (IcedTea6 1.10.2) (6b22-1.10.2-0ubuntu1~11.04.1)
OpenJDK 64-Bit Server VM (build 20.0-b11, mixed mode)
```The CLASSPATH environment variable is blank. Does anyone know how I'm supposed to set this up so my program will compile? 
Thanks in advance.
A JAR file is mostly a ZIP, you can list its contents with 
```
zip -l [file]
```And you should find a /netscape/javascript directory in it, wth the .class files of the package.

To add the JAR to your classpath:```
javac -cp /path/to/your.jar [source files]
```

---

### Post by jpr0 on 2011-09-08
Hi, thanks for the reply. I managed to get it going by unzipping that archive and including netscape/ into the source directory.

---

### Post by ofnuts on 2011-09-08
> **jpr0 said:**
> Hi, thanks for the reply. I managed to get it going by unzipping that archive and including netscape/ into the source directory.
Wtong way. Keep the jar and add it to the class path. I'm a bit surprised at the package name, though. Normally package names are "inverse net names" to insure uniqueness, so the "netscape" package would really be a "com.netscape" or somesuch (and the jar would contain /com/netscape/some.class).

---

### Post by jpr0 on 2011-09-08
I tried using -cp with a path to the jar containing the netscape class, but I got some compilation errors. Extracting the jar was the only way I could do it.

---

### Post by ofnuts on 2011-09-09
> **jpr0 said:**
> I tried using -cp with a path to the jar containing the netscape class, but I got some compilation errors. Extracting the jar was the only way I could do it.
Yes, but doing so is likely masking problems. If you can't compile with -cp, you can't run it -cp either. Where I can I find the jar with the netscape package on the web?

---

### Post by jpr0 on 2011-09-09
> **ofnuts said:**
> Yes, but doing so is likely masking problems. If you can't compile with -cp, you can't run it -cp either. Where I can I find the jar with the netscape package on the web?

I've no idea... just look for "plugin.jar" on your computer, for me it was here "/usr/share/icedtea-web/plugin.jar". I can't find where it is supposed to be installed. I read on other forums you could find it in "JAWS.jar" and a couple of other jars, but I couldn't find any of those.

---

### Post by ofnuts on 2011-09-09
> **jpr0 said:**
> I've no idea... just look for "plugin.jar" on your computer, for me it was here "/usr/share/icedtea-web/plugin.jar". I can't find where it is supposed to be installed. I read on other forums you could find it in "JAWS.jar" and a couple of other jars, but I couldn't find any of those.If you code si an applet, I assume you want other folks to run it. If  you can't tell where to get the necessary libs from, you won't get many  users...

---

### Post by jpr0 on 2011-09-10
> **ofnuts said:**
> If you code si an applet, I assume you want other folks to run it. If  you can't tell where to get the necessary libs from, you won't get many  users...

Actually it's only going to have a handful of users anyway. The code works fine on all the systems I tried it on so far... Once it's compiled into a .class or .jar, then isn't all the necessary binary code included within that one file?

---

### Post by ofnuts on 2011-09-10
> **jpr0 said:**
> Actually it's only going to have a handful of users anyway. The code works fine on all the systems I tried it on so far... Once it's compiled into a .class or .jar, then isn't all the necessary binary code included within that one file?The .class only contains the code of a .java. Your own .jar can contain classes you lifted from plugins.jar but this is very bad practice for way too many reasons.

---

### Post by jpr0 on 2011-09-10
> **ofnuts said:**
> The .class only contains the code of a .java. Your own .jar can contain classes you lifted from plugins.jar but this is very bad practice for way too many reasons.

Well, in the absence of any other method, I have to do this. The jar I used was located in the iced-tea plug-in install directory. If I link to this, then doesn't my code assume that the other computer also has this plugin? I really cannot find out which jar this is supposed to be in, and where that jar would be on a standard Java install. This page: 

[http://www.jarfinder.com/index.php/jars/jarClasses/9](http://www.jarfinder.com/index.php/jars/jarClasses/9)

indicates that I need plugin.jar but this is nowhere to be found on my computer except for the iced-tea directory.

-------
Edit:
-------

I installed the sun JRE and the file is located here: /usr/lib/jvm/java-6-sun-1.6.0.26/jre/lib/plugin.jar 
So now I can compile the code using  javac -cp /usr/lib/jvm/java-6-sun-1.6.0.26/jre/lib/plugin.jar myfile.java
So now how can I specify the CLASSPATH environment variable so that I don't have to compile with the cp argument each time?

---

### Post by ofnuts on 2011-09-10
> **jpr0 said:**
> Well, in the absence of any other method, I have to do this. The jar I used was located in the iced-tea plug-in install directory. If I link to this, then doesn't my code assume that the other computer also has this plugin? I really cannot find out which jar this is supposed to be in, and where that jar would be on a standard Java install. This page: 

[http://www.jarfinder.com/index.php/jars/jarClasses/9](http://www.jarfinder.com/index.php/jars/jarClasses/9)

indicates that I need plugin.jar but this is nowhere to be found on my computer except for the iced-tea directory.

-------
Edit:
-------

I installed the sun JRE and the file is located here: /usr/lib/jvm/java-6-sun-1.6.0.26/jre/lib/plugin.jar 
So now I can compile the code using  javac -cp /usr/lib/jvm/java-6-sun-1.6.0.26/jre/lib/plugin.jar myfile.java
So now how can I specify the CLASSPATH environment variable so that I don't have to compile with the cp argument each time?

See: 
[http://download.oracle.com/javase/1.4.2/docs/tooldocs/solaris/classpath.html](http://download.oracle.com/javase/1.4.2/docs/tooldocs/solaris/classpath.html)

But I'm surprised you have neither a script nor a makefile to run your compiles yet...

---

