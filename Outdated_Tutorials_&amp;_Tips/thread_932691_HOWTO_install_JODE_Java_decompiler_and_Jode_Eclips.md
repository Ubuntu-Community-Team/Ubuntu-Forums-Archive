---
title: "HOWTO: install JODE Java decompiler and Jode Eclipse Plugin"
date: 2008-09-28
forum: Outdated Tutorials &amp; Tips
---

### Post by gasull on 2008-09-28
[JODE (Java Optimize and Decompile Environment)]("http://jode.sourceforge.net/") seems to be the [best Java decompiler available]("http://www.program-transformation.org/Transform/DecompilationJodeTest#Conclusion").  But the installation of JODE and JodeEclipse is far from straightforward:

[LIST]
[*]**NB:** The JODE Makefile created a wrong executable that I needed to modify.
[*]**NB:** The JodeEclipse plugin you get from the [update server said at JodeEclipse website]("http://blog.technoetic.com/open-source/jode-eclipse-plugin/") doesn't work (at least it didn't for me with Eclipse 3.4).
[/LIST] 

I decided to write this tutorial after successfully installing them.

[LIST=1]
[*]Install Java Getopt: ```
sudo aptitude install libgetopt-java
```
[*][Download the JODE JAR file from SourceForge]("http://sourceforge.net/project/showfiles.php?group_id=3790"). We need just the .jar, not the .tar.gz.
[*]Place the JODE JAR in /usr/local/share/java/:
```

sudo mkdir /usr/local/share/java #If it doesn't exists yet
sudo chmod 755 /usr/local/share/java
sudo cp jode-1.1.2-pre1.jar /usr/local/share/java/
sudo chmod 644 /usr/local/share/java/jode-*.jar

```
[*]Create the jode executable:
```
sudo gedit /usr/local/bin/jode #Or with Vim, etc.
```
Write this in the editor:
```

#!/bin/bash
prefix=/usr/local

case $1 in
  [Ss]wi*) CLAZZ=jode.swingui.Main; shift ;;
  [Dd]ec*) CLAZZ=jode.decompiler.Main; shift ;;
  [Oo]bf*) CLAZZ=jode.obfuscator.Main; shift ;;
	*) CLAZZ=jode.decompiler.Main ;;
esac

#CP=`echo $CLASSPATH | sed s/:/,/`
CLASSPATH=${prefix}/share/java/jode-1.1.2-pre1.jar:/usr/share/java/gnu-getopt.jar:.
echo Executing: /usr/bin/java -classpath $CLASSPATH $CLAZZ $*
/usr/bin/java -classpath $CLASSPATH $CLAZZ $*

```
And give it the right permissions once the you close the file:
```
sudo chmod 755 /usr/local/bin/jode
```
[*]We already have JODE installed.  Now we [get JodeEclipse plugin from SourceForge]("http://sourceforge.net/projects/jodeeclipse").
[*]Place the plugin into the Eclipse plugin directory:
```
sudo cp net.sourceforge.jode_1.0.6.jar /usr/lib/eclipse/plugins/
```
[/LIST]

That's all.  You might be interested also in installing the [Bytecode Outline plugin from ASM ObjectWeb]("http://asm.objectweb.org/eclipse/index.html"), specially for those classes that JODE fails to decompile.

HTH.

---

### Post by davidgaya on 2009-04-22
Thanks very much, you save me a lot of time. 


[SIZE=2]**How to build and install edge JODE**[/SIZE]

**junit** package is a requirement to run tests
```
sudo aptitude install junit
```**htp** package is a requirement to build documentation
```
sudo aptitude install htp
```Check your java compiler version is at least 1.2
```
javac -version
```Download last svn trunk
```
svn co https://jode.svn.sourceforge.net/svnroot/jode/trunk/jode jode
```Go into downloaded directory
```
cd jode
```Build java files into class files
```
ant build
```Run tests to see everything is correct
```
ant test
```Build jar files
```
ant release-bindist
```Your newly created jode file is in 
release/jode-1.90-CVS/jode.jar

Follow gasull instructions except that there is an important change.
[B]
Note ![/B]
 Jode java classes are in net.sf.jode.* path.
 You must modify script to something like this:
```

!/bin/bash
prefix=/usr/local

case $1 in
  [Ss]wi*) CLAZZ=net.sf.jode.swingui.Main; shift ;;
  [Dd]ec*) CLAZZ=net.sf.jode.decompiler.Main; shift ;;
  [Oo]bf*) CLAZZ=net.sf.jode.obfuscator.Main; shift ;;
    *) CLAZZ=net.sf.jode.decompiler.Main ;;
esac

#CP=`echo $CLASSPATH | sed s/:/,/`
CLASSPATH=${prefix}/share/java/jode.jar:/usr/share/java/gnu-getopt.jar:.
#echo Executing: /usr/bin/java -classpath $CLASSPATH $CLAZZ $*
/usr/bin/java -classpath $CLASSPATH $CLAZZ $*

```

---

