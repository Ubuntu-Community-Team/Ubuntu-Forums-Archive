---
title: "Scite, javac and $CLASSPATH"
date: 2009-10-05
forum: Programming Talk
---

### Post by spadewarrior on 2009-10-05
Hello. 

I'm having a problem compiling java code from inside Scite ('Compile' option) when the code wants to import anything that is referred to from my $CLASSPATH. The same code compiles fine with the command javac from the terminal.

Here is the code I tried to get Scite to compile (JUnit is installed and referenced in my $CLASSPATH in my .bashrc file)



[PHP]
import junit.framework.*; 
public class JUnitTest
{
    
    
    
    
}[/PHP]

Compiling it in Scite fails. Here is the verbose output from Scite:

```
>javac JUnitTest.java -verbose
[parsing started JUnitTest.java]
[parsing completed 65ms]
[search path for source files: .]
[search path for class files: /usr/lib/jvm/java-6-openjdk/jre/lib/resources.jar,/usr/lib/jvm/java-6-openjdk/jre/lib/rt.jar,/usr/lib/jvm/java-6-openjdk/jre/lib/sunrsasign.jar,/usr/lib/jvm/java-6-openjdk/jre/lib/jsse.jar,/usr/lib/jvm/java-6-openjdk/jre/lib/jce.jar,/usr/lib/jvm/java-6-openjdk/jre/lib/charsets.jar,/usr/lib/jvm/java-6-openjdk/jre/lib/rhino.jar,/usr/lib/jvm/java-6-openjdk/jre/classes,/usr/lib/jvm/java-6-openjdk/jre/lib/ext/localedata.jar,/usr/lib/jvm/java-6-openjdk/jre/lib/ext/sunjce_provider.jar,/usr/lib/jvm/java-6-openjdk/jre/lib/ext/gnome-java-bridge.jar,/usr/lib/jvm/java-6-openjdk/jre/lib/ext/dnsns.jar,/usr/lib/jvm/java-6-openjdk/jre/lib/ext/pulse-java.jar,/usr/lib/jvm/java-6-openjdk/jre/lib/ext/sunpkcs11.jar,.]
JUnitTest.java:1: package junit.framework does not exist
import junit.framework.*; 
^
[loading java/lang/Object.class(java/lang:Object.class)]
[checking JUnitTest]
[total 497ms]
1 error
>Exit code: 1


```

From the terminal, the same command works. The difference is that the information in my $CLASSPATH is actually used:

```
[parsing started JUnitTest.java]
[parsing completed 62ms]
[search path for source files: /home/sean/java/JGame/jgame-jogl.jar,/home/sean/java/GTGE/golden_0_2_3.jar,/usr/share/java/junit.jar,/usr/share/java/junit4-4.3.1.jar,.]
[search path for class files: /usr/lib/jvm/java-6-openjdk/jre/lib/resources.jar,/usr/lib/jvm/java-6-openjdk/jre/lib/rt.jar,/usr/lib/jvm/java-6-openjdk/jre/lib/sunrsasign.jar,/usr/lib/jvm/java-6-openjdk/jre/lib/jsse.jar,/usr/lib/jvm/java-6-openjdk/jre/lib/jce.jar,/usr/lib/jvm/java-6-openjdk/jre/lib/charsets.jar,/usr/lib/jvm/java-6-openjdk/jre/lib/rhino.jar,/usr/lib/jvm/java-6-openjdk/jre/classes,/usr/lib/jvm/java-6-openjdk/jre/lib/ext/localedata.jar,/usr/lib/jvm/java-6-openjdk/jre/lib/ext/sunjce_provider.jar,/usr/lib/jvm/java-6-openjdk/jre/lib/ext/gnome-java-bridge.jar,/usr/lib/jvm/java-6-openjdk/jre/lib/ext/dnsns.jar,/usr/lib/jvm/java-6-openjdk/jre/lib/ext/pulse-java.jar,/usr/lib/jvm/java-6-openjdk/jre/lib/ext/sunpkcs11.jar,/home/sean/java/JGame/jgame-jogl.jar,/home/sean/java/GTGE/golden_0_2_3.jar,/usr/share/java/junit.jar,/usr/share/java/junit4-4.3.1.jar,.]
[loading java/lang/Object.class(java/lang:Object.class)]
[checking JUnitTest]
[wrote JUnitTest.class]
[total 524ms]

```

Does anyone know how I can get Scite to read my $CLASSPATH jars?

Thanks!

=)

---

### Post by invisisci on 2009-12-27
Did you ever solve this problem, Spadewarrior?

I am having a very similar issue (command works fine in shell, but not as a scite command), and am scratching my head about how to solve it. I can run "env" in scite and see that scite doesn't have all my environment variables set, but I don't know how to fix it :-/

---

### Post by spadewarrior on 2009-12-27
'Fraid not. I just settled for compiling from the command line. If you solve this, can you add the solution to this thread?

---

### Post by matsuzine on 2009-12-28
Okay, give this a try...

To add customization to the compile or build steps in scite, you need to edit one of the properties files.  Here's what I did to customize the classpath:

Under 'Options' menu, select 'Open Local Options File'.  You should see an empty file if you haven't made any customizations.

Add a command like this one to the file:

```
command.compile.*.java=javac -cp /path/to/your/classes/library.jar $(FileName).java
```Save the file, and you should be able to compile.  

Check out the docs for Scite at [http://www.scintilla.org/SciTEDoc.htm]("http://www.scintilla.org/SciTEDoc.html")l for more ideas on customizing build options!

Hope it helps!

---

### Post by spadewarrior on 2009-12-29
Yep, that works. Thanks very much for that!

---

