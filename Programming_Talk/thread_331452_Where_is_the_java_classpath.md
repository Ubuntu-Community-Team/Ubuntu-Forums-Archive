---
title: "Where is the java classpath?"
date: 2007-01-04
forum: Programming Talk
---

### Post by xpan on 2007-01-04
hi,

I am new to Linux (Ubuntu 6.10) and I would like to program in Java. 

In windows I was able to modify the environment variable CLASSPATH to point to the jar file I would like to use. 

How can I do such a thing in Linux? 

PS: more specifically I would like to add the "javac.comm" api

---

### Post by pmasiar on 2007-01-04
i guess answer is here: [http://www.ubuntuforums.org/showpost.php?p=725746&postcount=9](http://www.ubuntuforums.org/showpost.php?p=725746&postcount=9)

---

### Post by welshboy on 2007-01-04
I also learned another thing just now as a matter of fact.

According to a book I'm reading, you could put the .jar files into a folder called ext in your java folders, which will be here (if you installed from repos)

/usr/lib/jvm/java-1.5.0-sun-1.5.0.08/jre/lib/ext$


According to my book at least, it means that the .jars will be found automatically by the compiler.

However I think you'd need to be a super user to copy files to it

so you'd do
emyr@Wookie:~$sudo cp util.jar /usr/lib/jvm/java-1.5.0-sun-1.5.0.08/jre/lib/ext$

And then that should prompt you for your password, and then copy the jar file to the folder.  Then you'll be able to access the jar file in all your java programs.

To edit the CLASSPATH variable, you could either edit your .bashrc if you want to make it just for your user, or the whole system by editing etc/environment

Hope that helps a bit too :S

Again, I'm going by what the book tells me.

---

### Post by steve.horsley on 2007-01-05
welshboy is right. It is best not to set the classpath. Put "library" jar files like javax.comm in the JVM's extensions directory.

---

### Post by theDaveTheRave on 2008-11-27
THANKS

> **welshboy said:**
> I also learned another thing just now as a matter of fact.

According to a book I'm reading, you could put the .jar files into a folder called ext in your java folders, which will be here (if you installed from repos)

/usr/lib/jvm/java-1.5.0-sun-1.5.0.08/jre/lib/ext$


According to my book at least, it means that the .jars will be found automatically by the compiler.

However I think you'd need to be a super user to copy files to it

so you'd do
emyr@Wookie:~$sudo cp util.jar /usr/lib/jvm/java-1.5.0-sun-1.5.0.08/jre/lib/ext$



I could kiss you....

I've been fighting trying to get my ConnectorJ to work.

and I've been searching everywhere for 2 days nearly, as soon as I did this.... :guitar:


What I would like to know....

if it was such a simple thing, why is it that on the MySQL site and on all the other forums they are saying that you need to edit the classpath and stuff.... which for me didn't work!

I still need to test on my other system, where the classpath and stuff is just set on a temporary basis.... I'll try it in a bit..

and report back, then i'll need to play with all the other threads i have open on MySQL and the Java forums (and on the Ubuntu's)... and put a note in my own personal help file!!!


David


ps. Again Welshboy... you are beautifull... what is the title of that book - I think I want a copy!

---

### Post by jespdj on 2008-11-27
> **theDaveTheRave said:**
> if it was such a simple thing, why is it that on the MySQL site and on all the other forums they are saying that you need to edit the classpath and stuff.... which for me didn't work!
Putting all kinds of libraries in jre/lib/ext is not recommended, because these libraries will now be loaded for every Java application that you load - and sometimes that is not what you want, especially if a Java application has a different version of the same libraries (the lib you'd have in jre/lib/ext could interfere with the application, leading to weird and hard to solve problems).

You can set the classpath of a Java application on the commandline with the "-cp" switch:
```
# Compile with:
javac -cp blabla.jar:. MyProgram.java

# Run with:
java -cp blabla.jar:. MyProgram

```
Or you can set the CLASSPATH environment variable in your **.profile**, for example. Add a line like this to .profile:
```
export CLASSPATH=/home/user/bla/blabla.jar:.
```
(Log out and back in again to make sure it's activated).

Note that entries in the classpath are separated with ':', and '.' means "the current directory".

---

### Post by theDaveTheRave on 2008-12-01
jespdj,

I can confirm that my classpath and "normal" path are as they should be (according to the documentation from MySQL, on the Sun site and various forums)

```

davem@Dartagnon:~$ echo $PATH
/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/home/davem/downloads/mysql-connector-java-5.1.7/mysql-connector-java-5.1.7-bin.ja
davem@Dartagnon:~$ echo $CLASSPATH
/home/davem/.netbeans/6.0/modules/ext/mysql-connector-java-5.0.7-bin.jar:/usr/share/java/mysql-connector-java-5.1.5.jar:/usr/share/java/mysql-connector-java-5.1.5:/home/davem/downloads/mysql-connector-java-5.1.7/mysql-connector-java-5.1.7-bin.jar
davem@Dartagnon:~$ 

```

however, until I added the connectorJ to the folder mentioned by WelshBoy my little application failed persistently with a <javaClassNotFoundException> which was highly aggravating.

As this is an important part of what I am currently working on if I add this connectorJ to the same directory on all the terminals that may run this applet I can at least guarantee that my applications will work!

I guess I could try your method of setting the classpath at compile time, but I still wouldn't know if the file was in the correct place on another client machine.

What happen also when you have multiple users on a system? can they each have different classpath activations? I have read that if I set the classpath on the command line, it will only be set for the period that that terminal is open, so running an application by a double click from nautilus will still mean it may not function.

To be honest, as the connectorJ that is in the repositories is preety muh up to date I am surprised that simply <apt-get>ing it didn't make it work?

Is this an issue that only I have had or is this a common difficulty for all Java newbie developers?

David

---

### Post by mayaofr on 2011-09-12
I got the similar things.

I got the error: java.sql.exceptions: no suitable driver found for.

I don't know what is wrong, because I used the newest jdbc driver: ojdbc14.jar

```
$ echo $JAVA_HOME
/usr/java/jdk1.6
```

and also i use the classpath:```
$ echo $JAVA_HOME
/usr/java/jdk1.6
```

I run the java application, and in the logs, it found that ojdbc14.jar, but still, there is the exception: no suitable driver.
Someone said, it is because this is not the safe path, normarlly you shall set to /usr/lib/jvm/jdk1.6, i don' t understand.

what shall I do?

---

### Post by ofnuts on 2011-09-12
> **theDaveTheRave said:**
> 
if it was such a simple thing, why is it that on the MySQL site and on all the other forums they are saying that you need to edit the classpath and stuff.... which for me didn't work!!
Maybe because you didn't do it correctly...putting the .JAR in ext is just avoiding the problem (and creating several others), not solving it.

---

### Post by theDaveTheRave on 2011-10-04
ofnuts,

so can you point out where in the output of my
$path
and 
$classpath

variables the problem is?

What I have taken to doing is having a single location on my HDD (under home) where I store the various downloaded .jar files. Then from within my IDE I set the "classpath" to import the required libraries for me. this seems to work out,  guess it is adding in the <-cp location> into the auto created manifest... which I mostly try to ignore!

Davd

---

### Post by ofnuts on 2011-10-04
> **theDaveTheRave said:**
> ofnuts,

so can you point out where in the output of my
$path
and 
$classpath

variables the problem is?

What I have taken to doing is having a single location on my HDD (under home) where I store the various downloaded .jar files. Then from within my IDE I set the "classpath" to import the required libraries for me. this seems to work out,  guess it is adding in the <-cp location> into the auto created manifest... which I mostly try to ignore!

Davd

The "/usr/share/java/mysql-connector-java-5.1.5" without  a .JAR at the end is incorrect, but shouldn't harm. But here is a mix of versions which is worrisome...

Classpath problems are usually fairly simple to solve, when you answer the real questions:

1) which class is causing the ClassNotFound Exception
2) where is it really (in what JAR, and with what path) (use "unzip -l" agains the JARs to find it)
3) how did you put the .JAR in the classpath. This may have different answers between trial runs in your IDE (Eclipse, NetBeans...) and running the final app (starting java from a terminal or a script)

---

