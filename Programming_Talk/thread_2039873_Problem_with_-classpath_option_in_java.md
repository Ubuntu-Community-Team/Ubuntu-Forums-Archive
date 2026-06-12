---
title: "Problem with -classpath option in java"
date: 2012-08-09
forum: Programming Talk
---

### Post by OzzyEazy on 2012-08-09
Hi, 

I'm trying to use a jar file in my program by using the -cp option in Java. The funny thing is compiling seems to work this way but not running it. 

I do:

javac -cp <path to jar file> MyProgram.java
(That works)
java -cp <path to jar file> MyProgram
And then it says java.lang.NoClassDefFoundError and java.lang.ClassNotFoundException.

I'm kind of a newbie in all this and I'm doing a course on OOP in Java. For an exercise I was required to include a class from a jar file.

Could someone please help me out with this?

---

### Post by andrewc6l on 2012-08-09
Your classpath will need to include both the jar file and the directory that contains MyProgram (assuming it's in the default package). For example:
```
java -cp foo.jar:. MyProgram
```

More info than you ever wanted is here:
[http://www.ibm.com/developerworks/library/j-classpath-unix/](http://www.ibm.com/developerworks/library/j-classpath-unix/)

---

### Post by OzzyEazy on 2012-08-09
I think I'm doing that. I entered
java -classpath ~/Java/verkiezingen.jar Verkiezingsprogramma

I also tried
java -classpath ~/Java/verkiezingen ~/Java/Verkiezingsprogramma

And that spits out the same result.

---

### Post by ofnuts on 2012-08-10
> **OzzyEazy said:**
> I think I'm doing that. I entered
java -classpath ~/Java/verkiezingen.jar Verkiezingsprogramma

I also tried
java -classpath ~/Java/verkiezingen ~/Java/Verkiezingsprogramma

And that spits out the same result.
Is there a "package" definition in your class? If so you have to move it to the appropriate directory, ie if your source file says 
```

package foo;

```
Then when starting execution, you should have a directory "foo" with your Verkiezingsprogramma.class in it, and start the program with:
```

java -cp {jars list} foo/Verkiezingsprogramma

```
In other words, the "package" declaration implies a positiong of the .class in a directory tree (this is relative to any jar/directory listed in the class path).

---

### Post by dwhitney67 on 2012-08-10
> **ofnuts said:**
> 
```

java -cp {jars list} foo/Verkiezingsprogramma

```


Actually, that would be:
```

java -cp (jars list) foo.Verkiezingsprogramma

```

---

### Post by ofnuts on 2012-08-10
> **dwhitney67 said:**
> Actually, that would be:
```

java -cp (jars list) foo.Verkiezingsprogramma

```Yup.

---

### Post by trent.josephsen on 2012-08-10
> **dwhitney67 said:**
> Actually, that would be:
```

java -cp (jars list) foo.Verkiezingsprogramma

```

Don't both versions work? I have been using them interchangeably. Is there a difference?

---

### Post by dwhitney67 on 2012-08-10
> **trent.josephsen said:**
> Don't both versions work? I have been using them interchangeably. Is there a difference?

I stand corrected; I wrote a little test application, and it seems that you are correct.

P.S.  I did not test this application under Windows.  So I don't know if the slash-notation works there as well.

---

### Post by OzzyEazy on 2012-08-10
> **ofnuts said:**
> Is there a "package" definition in your class? If so you have to move it to the appropriate directory, ie if your source file says 
```

package foo;

```
Then when starting execution, you should have a directory "foo" with your Verkiezingsprogramma.class in it, and start the program with:
```

java -cp {jars list} foo/Verkiezingsprogramma

```
In other words, the "package" declaration implies a positiong of the .class in a directory tree (this is relative to any jar/directory listed in the class path).

I'm assuming there's a package definition in the class I'm trying to use since it's in the jar file I was given. There's no package definition in my own (main) class.

basically there's a java file that uses a .class from a jar file which is in the same directory. While in this directory I go 

javac -cp ~/Somewhere/something.jar MyProgram.java 

and that, seemingly, works. Then I try running the program 

java -cp ~/Somewhere/something.jar MyProgram 

and it says 

Exception in thread "main" java.lang.NoClassDefFoundError: /home/oscar/Java/Verkiezingsprogramma
Caused by: java.lang.ClassNotFoundException: .home.oscar.Java.Verkiezingsprogramma
	at java.net.URLClassLoader$1.run(URLClassLoader.java:217)
	at java.security.AccessController.doPrivileged(Native Method)
	at java.net.URLClassLoader.findClass(URLClassLoader.java:205)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:321)
	at sun.misc.Launcher$AppClassLoader.loadClass(Launcher.java:294)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:266)
Could not find the main class: /home/oscar/Java/Verkiezingsprogramma. Program will exit.

I tried typing the entire path for MyProgram on execution, same results.

---

### Post by ofnuts on 2012-08-11
The class name should always be relative (in fact it is relative to all directories and roots of jar files given in the classpath (and the classpath implicitly contains the working directory). So /home/you/java/whatever/Someclass is never a good specification to start a Java program. If your working directory is "/home/your/java/" then use "whatever.Someclass".

---

### Post by dwhitney67 on 2012-08-11
> **OzzyEazy said:**
> 
java -cp ~/Somewhere/something.jar MyProgram 


You were advised earlier (by andrewc6l) to also include the current directory in your classpath specification.  The command above still fails to do that.

Try:
```

java -cp ~/Somewhere/something.jar:. MyProgram

```
Notice the :. at the end of the classpath statement.

---

