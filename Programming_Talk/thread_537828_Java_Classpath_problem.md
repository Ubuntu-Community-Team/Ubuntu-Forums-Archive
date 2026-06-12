---
title: "Java Classpath problem"
date: 2007-08-29
forum: Programming Talk
---

### Post by ubermike on 2007-08-29
I have created a jar(test.jar) that relies on a third party library(jgraph.jar). My test.jar has the following manifest:

[COLOR="Blue"]Manifest-Version: 1.0
Ant-Version: Apache Ant 1.6.5
Created-By: 1.5.0_11-b03 (Sun Microsystems Inc.)
Built-By: ubermike
Main-Class: org.ubermike.TestJGraph
Class-Path: jgraph.jar[/COLOR]

When I try to run it using any of the following formats I get the same error - NoClassDefFound:

java -jar test.jar
java -cp ./lib/jgraph.jar -jar test.jar
java -classpath ./lib/jgraph.jar -jar test.jar

I have tried setting the CLASSPATH with no effect:
export CLASSPATH=./lib/jgraph.jar or export CLASSPATH=./lib

Does anybody have any ideas?

---

### Post by samjh on 2007-08-29
The Class-Path option in your manifest needs to specify the path to your jgraph.jar file.

So if your jgraph.jar file is located in ./lib relative to your test.jar file, it should be:```
Class-Path: ./lib/jgraph.jar
```

If you're running the test.jar file by hand, do this:
```
java -cp ./lib/jgraph.jar:. -jar test.jar
```

When you specify classpaths explicitly, you need to specify the locations of the dependencies, as well as the class you want to run.

---

### Post by ubermike on 2007-08-29
Made change to MANIFEST but get the same results.

I have also reviewed the contents of the jgraph.jar to confirm it does contain the class that I require.

Any other ideas? 

It appears that no matter what I do the classpath is disregarded.

---

### Post by samjh on 2007-08-29
Exactly what is in your test.jar file?  How are the files organised within?

---

### Post by ubermike on 2007-08-29
test.jar :
META-INF/MANIFEST.MF
org/ubermike/TestJGraph.class
lib/jgraph.jar

This version has the "lib/jgraph.jar" but it should not make a difference. I have tried it without.

---

### Post by samjh on 2007-08-29
You cannot access a jar file stored within a jar file.

What you need to do is take the jgraph.jar file out of there, and put it into a directory named /lib.  Then your manifest can say Class-Path ./lib/jgraph.jar and it will work.

Otherwise, extract everything in jgraph.jar, and then re-pack the TestJGraph class into a /org/ubermike/ directory within your test.jar file.  Your manifest should then specify Class-Path /org/ubermike/TestJGraph (I think, I haven't done this in ages).

As an example of the first method, here's what a recursive directory listing (using ls -R) looks like in a small project of mine:
```
.:
gametute.jar  lib

./lib:
GTGE.jar  player.png
```gametute.jar contains my main class: GameTute.class file.  But it depends on GTGE.jar, which resides in a /lib directory outside of my gametute.jar, because Java doesn't allow you to access a jar within a jar.

---

### Post by ubermike on 2007-08-29
Sorry, no luck. It still throws same exception

~/Projects/TestJGraph$ java -jar test.jar
Exception in thread "main" java.lang.NoClassDefFoundError: org/jgraph/graph/GraphModel
~/Projects/TestJGraph$ java -cp .:./lib/jgraph.jar -jar test.jar
Exception in thread "main" java.lang.NoClassDefFoundError: org/jgraph/graph/GraphModel

I have attached my test.jar (had to name it test.zip)

---

### Post by ubermike on 2007-08-29
The MANIFEST.MF identifies that the jar was built with [COLOR="Blue"]1.5.0_11-b03 (Sun Microsystems Inc.)[/COLOR]

Below is the output from [COLOR="Blue"]java -version[/COLOR] on command line:
~/Projects/TestJGraph$ java -version
java version "1.5.0_11"
Java(TM) 2 Runtime Environment, Standard Edition (build 1.5.0_11-b03)
Java HotSpot(TM) Client VM (build 1.5.0_11-b03, mixed mode, sharing)

---

### Post by samjh on 2007-08-29
To clarify: your program is TestJGraph, right?  TestJGraph belongs to org.ubermike package?  And TestJGraph depends on the jgraph.jar library?

If my assumptions are true, your test.jar file and its manifest looks OK.

What I find puzzling is this:
```
~/Projects/TestJGraph$ java -jar test.jar
Exception in thread "main" java.lang.NoClassDefFoundError: **org/jgraph/graph/GraphModel**
```Why is Java trying to locate the "main" method in org.jgraph.graph.GraphModel?!  According to your manifest, it should be pointing to org.ubermike.TestJGraph!

I need to sleep.  Hopefully someone with a fresher mind will help you out soon enough. ;)

---

### Post by ubermike on 2007-08-29
Yes, the program is TestJGraph.

Actually, it is running main from TestJGraph but the problem arises from the following line:

 *[COLOR="Blue"]GraphModel model = new DefaultGraphModel();[/COLOR]*

That is the first line in the main method.

---

### Post by pbrockway2 on 2007-08-30
What is the manifest you are using?  

It is important to confirm that you are running the main method of the class you think you are, and that the classpath is what you think it is.  This information comes from the manifest. (and the manifest is fussy about things like line length and new lines.)

See, for example [http://java.sun.com/docs/books/tutorial/deployment/jar/downman.html](http://java.sun.com/docs/books/tutorial/deployment/jar/downman.html)

Incidently, I don't think the -cp switch has any effect if you use the -jar switch.  Ie, the classpath is exactly what the Class-Path manifest entry says it is.

---

### Post by ubermike on 2007-08-30
Attached is my MANIFEST.

[INDENT][COLOR="Blue"]Manifest-Version: 1.0
Ant-Version: Apache Ant 1.6.5
Created-By: 1.5.0_11-b03 (Sun Microsystems Inc.)
Built-By: ubermike
Main-Class: org.ubermike.TestJGraph
Class-Path: ./lib/jgraph.jar

[/COLOR][/INDENT]

Note : There are actually two blank lines after the Class-Path line.

Actually, I had already read that the -cp on the command line should have not effect. I was trying it because nothing else seems to be working.

---

### Post by pbrockway2 on 2007-08-31
Sorry, I've just realised that you already posted the manifest...

Anyway I downloaded jgraph, and your jar file and had a play.  I got the same error as you - even tried lots of variations with the manifest.  It's late here, so maybe I'm missing something obvious.

The following, however, does work fine.  It doesn't use the manifest, and is essentially what they say to do on the jgraph web site

```
java -cp ./test.jar:./lib/jgraph.jar org.ubermike.TestJGraph
```

(I don't post here much so I hope I get the code tags right.)

---

