---
title: "[SOLVED] No JAVA_HOME Environment Variable?"
date: 2008-09-02
forum: Programming Talk
---

### Post by Jesdisciple on 2008-09-02
I'm not sure if this should be here or in General Help, so just move this if I'm wrong.

I'm trying to get [WebScarab]("http://www.owasp.org/index.php/Category:OWASP_WebScarab_Project") running smoothly, but it tells me on startup that> The JavaHelp libraries could not be found
Please add jhall.jar to the extension directory of your Java Runtime environmentSo I found jhall.jar in /usr/share/java and copied it to all three possible extension directories (/usr/lib/jvm/**[**java-6-openjdk | java-6-sun | java-6-sun-1.6.0.06**]**/jre/lib/ext) and the error message still came.  As I found out at [this other thread]("http://ubuntuforums.org/showthread.php?t=244896"), this works because of the JAVA_HOME environment variable.  Come to find out,```
$ echo $JAVA_HOME
[eerily blank line]
```And ~/.profile never mentions JAVA_HOME...  Shouldn't the Java installation have changed that?  Should I?

Thanks!

---

### Post by SeanHodges on 2008-09-02
Firstly, the JAVA_HOME environment variable only applies to the Java development kit ("JDK"), you do not need to set it to run normal Java applications, you only need it if you are developing in Java or running special server applications like Apache Tomcat.

After running the program and hitting the same problem, I took a look at the source code. It appears to have a fixed path for jhall.jar, which means it will only work if you do exactly this:

1) Make a directory called "lib" next to webscarab-selfcontained-20070504-1631.jar, assuming you have downloaded it to your desktop, this will be "/home/username/Desktop/lib"

2) Copy the jhall.jar into this directory.

3) Rename it to be "jhall-2.0_02.jar"

4) Try running the application again... java -jar webscarab-selfcontained-20070504-1631.jar


I have managed to prove that this works on my PC, post back if you still can't get it to work.

These instructions will also apply to Windows, I suggest this is a bug that the webscarab developers might not be aware of.

---

### Post by Jesdisciple on 2008-09-02
*slaps forehead*  I should have thought to try that.

WebScarab has a server, but of course that doesn't apply to this situation if the path is hard-coded.  Should I still set JAVA_HOME?  EDIT: And I do have the JDK installed.

And that fix doesn't work on this end.```
$ cd ~/Desktop
$ ls ./lib
jhall-2.0_02.jar
$ java -jar webscarab-selfcontained-20070504-1631.jar
The JavaHelp libraries could not be found
Please add jhall.jar to the extension directory of your Java Runtime environment
```

---

### Post by SeanHodges on 2008-09-03
Strange that it's not working for you. Its interesting that you found a jhall.jar in /usr/share/java - I couldn't find it here.

Perhaps you are running a version of the JVM that mismatches the version of jhall.jar you are trying to use... 

Try this:

1) Download jhall.jar from here: [http://www.java2s.com/Code/JarDownload/jhall.jar.zip](http://www.java2s.com/Code/JarDownload/jhall.jar.zip) (this is the copy that I got to work), replace the one in ./lib/ with this one (remember to rename it as well).

2) sudo update-alternatives --config java
Select OpenJDK 6 - "/usr/lib/jvm/java-6-openjdk/jre/bin/java"

3) Try it now, you will now have the exact same set-up as I do...


I do Java development, and have not set JAVA_HOME in my .profile or .bashrc. There are special cases when you might need to do this (e.g. you download a program that requires the whole JDK and is not packaged in APT), but most of the time it is handled by the launch script of the program itself. One reason for this is that you may switch to using a different JVM, but forget to change the JAVA_HOME accordingly.

---

### Post by jespdj on 2008-09-03
> **Jesdisciple said:**
> And ~/.profile never mentions JAVA_HOME...  Shouldn't the Java installation have changed that?  Should I?
The JDK itself does not need the JAVA_HOME environment variable, so that's why it's not set.

Some third-party software wants the JAVA_HOME environment variable to be set, to be able to find where your JDK or JRE is installed. You can just add it to your .profile yourself if necessary.

---

### Post by Jesdisciple on 2008-09-03
That did it; thanks!

EDIT:  See [this bogus bug report]("https://sourceforge.net/tracker/index.php?func=detail&aid=2091563&group_id=64424&atid=507433").

---

