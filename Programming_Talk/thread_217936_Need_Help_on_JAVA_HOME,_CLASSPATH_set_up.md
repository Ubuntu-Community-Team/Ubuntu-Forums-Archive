---
title: "Need Help on JAVA_HOME, CLASSPATH set up"
date: 2006-07-17
forum: Programming Talk
---

### Post by DapperDrakeNewbieDR on 2006-07-17
I need step-by-step instructions on how to set up the JAVA_HOME and CLASSPATH variables. Can anyone help me out with this issue?

Thanks in advance.

---

### Post by tedwardo2 on 2006-07-18
it depends on what implementation of java you have installed, where it is installed, and a number of other things.

If you already know what you want to set JAVA_HOME and CLASSPATH to, you can just run
```
sudo gedit /etc/environment
```
and then add a line for each variable.

---

### Post by DapperDrakeNewbieDR on 2006-07-18
Thanks tedwardo2, it worked perfectly fine.

See you around.

---

### Post by DapperDrakeNewbieDR on 2006-10-22
This is the output of the "etc/environment" file after I "gedit" it,

```

PATH="/usr/local/Java/jdk1.5.0_07/bin:.:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/bin/X11:/usr/games"
LANG="en_AU.UTF-8"
LANGUAGE="en_AU:en"
JAVA_HOME="/usr/local/Java/jdk1.5.0_07"
CLASSPATH="/usr/local/Java/jdk1.5.0_07/lib:."

```

It may serve you as a guide to you folks looking for help.

---

### Post by erpa on 2007-07-23
i'm having the same problem, but i don't know exactly what to do. i installed jdk and jre trough apt-get but i can't find "/usr/local/Java/jdk1.5.0_07/bin:." or any of the others path you used.
The best i was able to do was to find the java folder in usr/share but i can't find anything like jdk1.5.0_07/bin:. in it. This is the content of the java folder :

[[IMG]http://img527.imageshack.us/img527/1743/pippo2rn3.th.png[/IMG]](http://img527.imageshack.us/my.php?image=pippo2rn3.png)

wich path should i use? doi need to install somtging else? atm the content of my etc/environment is:

PATH="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games"
LANG="it_IT.UTF-8

thx in advice for help

P.S. sry for may bad english

---

### Post by steve.horsley on 2007-07-24
The easiest way to find it is to use the command 
**whcih java**
which probably says /usr/bin/java, but this is a symlink. if you do
**ls -l /usr/bin/java**
it will tell you where it links to (probably another symlink). Keep on followinf the symlinks until you find the real executable. It's there somewhere.

If you install java straight from Sun, it defaults into /opt/java..., but the Ubuntu packagers tend to put java in /usr/lib or /usr/share or something like that.

P.S.
With the Sun JRE, you don't normally need to set JAVA_HOME or CLASSPATH at all.

---

### Post by akhilanger on 2008-05-21
If you have installed java through sudo apt-get install ...... 
then it is installed in /usr/lib/jvm

---

### Post by bwakkie on 2008-06-30
euhm.. is my case:

which java
/usr/bin/java

ls -l /usr/bin/java
/usr/bin/java -> /etc/alternatives/java

ls -l /etc/alternatives/java
/etc/alternatives/java -> /usr/lib/jvm/java-gcj/jre/bin/java

Changed that to:
java -> /usr/lib/jvm/java-6-sun-1.6.0.06/jre/bin/java


then I added the following line to /etv/environment:
JAVA_HOME="/usr/lib/jvm/java-6-sun-1.6.0.06/"

and created the following symlink:
/usr/java/jdk -> /usr/lib/jvm/java-6-sun-1.6.0.06/

although I have both... java is sooooo confusing!!

---

### Post by elnur on 2008-09-15
> **bwakkie said:**
> 
Changed that to:
java -> /usr/lib/jvm/java-6-sun-1.6.0.06/jre/bin/java

and created the following symlink:
/usr/java/jdk -> /usr/lib/jvm/java-6-sun-1.6.0.06/


You really shouldn't. Just run this command:
```

sudo update-java-alternatives -s java-6-sun

```

It will set java-6-sun to be run by default.

---

### Post by Juzz on 2008-12-05
> **elnur said:**
> You really shouldn't. Just run this command:
```

sudo update-java-alternatives -s java-6-sun

```

It will set java-6-sun to be run by default.

Why does java on linux have to be so obscure?

I was wondering why my netbank didn't work anymore - but when I ran java --version gcj had stolen my settings from sun being default...

Even after running that command to set java alternatives firefox hangs and uses up 100% cpu time when trying to access my netbank :(

---

### Post by cl333r on 2008-12-05
> Why does java on linux have to be so obscure?
Historically due to licensing issues we had to install by default the gcj version which nobody took for serious including developers. Fortunately Java is (for a few years) on it's path to getting fully open source and the gcj version has been replaced with the openjdk version, which being better isn't yet as qualitative as the closed source one. But this continues changing to the better although no one can tell you when the day comes when openjdk is as good as the current closed version. There are plans to achieve this parity for Java 7.

---

### Post by Pathan on 2009-01-26
> **elnur said:**
> You really shouldn't. Just run this command:
```

sudo update-java-alternatives -s java-6-sun

```

It will set java-6-sun to be run by default.

Thanks mate it worked like a charm for me. :D I was unable to run a small monitoring application since 3 days. Thanks again

---

### Post by Zannax on 2009-07-10
> **elnur said:**
> You really shouldn't. Just run this command:
```

sudo update-java-alternatives -s java-6-sun

```

It will set java-6-sun to be run by default.

Thank you so much! :) I was stuck trying to install a software I absolutely need (personal income declaration) and it didn't work: I had no guess that gij was the problem. Now works like a charm!

---

### Post by elnur on 2009-07-10
> **Zannax said:**
> Thank you so much! :) I was stuck trying to install a software I absolutely need (personal income declaration) and it didn't work: I had no guess that gij was the problem. Now works like a charm!

You are totally welcome. :)

---

### Post by alex.scotton on 2009-11-09
AWESOME.... I have been messing with java for an hour or so until i stumbled across:
> sudo update-java-alternatives -s java-6-sun

Now to continue getting my own google wave server up and running haha... had to compile it with ant :-P

---

### Post by franciskus on 2010-03-01
I am facing a similar problem, when I try to run an application using Netbeans I receive a message that an specific package was not found.

I suppose it's because java is not finding the .jar in the classpath:
[PHP] private com.toedter.calendar.JDateChooser dataInicioFaturamento;
/home/francisco/NetBeansProjects/SikLami/src/com/sikgraf/ui/reports/ListagemFaturamentoUI.java:80: package com.toedter.calendar does not exist[/PHP]
This package is in the file **jcalendar-1.3.2.jar**, which is in **/home/francisco/Sistemas/lib10anos** folder. 

And I have my environment file as following:
[PHP]PATH="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games"
JAVA_HOME="/usr/lib/jvm/java-6-sun/jre"
CLASSPATH="/home/francisco/Sistemas/lib10anos:.:/home/francisco/Sistemas/lib10anos/jcalendar-1.3.2.jar"[/PHP]
Shouldn't be everything working correctly???

Appreciate any help.
F.

---

### Post by ubundom on 2010-03-02
Hi folks, I am trying to run (Serena) OpenProj [aka Projity] and it complains that it cannot find the [COLOR="Red"]saxon9-dom.jar[/COLOR]:

```
~$ openproj
Java auto-detection...
Checking java
    Java version: 1.6.0_15 OK
    Java implementation: Java(TM) OK
Java OK
Error 
  DOMSource cannot be processed: check that [COLOR="Red"]saxon9-dom.jar[/COLOR] is on the classpath
Exception in thread "main" java.lang.AssertionError: net.sf.saxon.trans.XPathException: DOMSource cannot be processed: check that [COLOR="Red"]saxon9-dom.jar[/COLOR] is on the classpath
	at java.util.prefs.XmlSupport.writeDoc(XmlSupport.java:262) ...

[COLOR="Orange"]<more stuff>[/COLOR]

... at net.sf.saxon.IdentityTransformer.transform(IdentityTransformer.java:29)
	at java.util.prefs.XmlSupport.writeDoc(XmlSupport.java:259)
	... 17 more
Error 
  DOMSource cannot be processed: check that saxon9-dom.jar is on the classpath
Exception in thread "Thread-1" java.lang.AssertionError: net.sf.saxon.trans.XPathException: DOMSource cannot be processed: check that [COLOR="Red"]saxon9-dom.jar[/COLOR] is on the classpath
	at java.util ...

[COLOR="Orange"]<more stuff>[/COLOR]

... Caused by: net.sf.saxon.trans.XPathException: DOMSource cannot be processed: check that [COLOR="Red"]saxon9-dom.jar[/COLOR] is on the classpath
	at net.sf.saxon.event.Sender.send(Sender.java:226)
	at net.sf.saxon.IdentityTransformer.transform(IdentityTransformer.java:29)
	at java.util.prefs.XmlSupport.writeDoc(XmlSupport.java:259)
	... 19 more
~$
```

But it seems to me that the saxon9-dom.jar is on the CLASSPATH:

```
~$ locate saxon9-dom
/usr/share/Kernow/lib/saxon9-dom.jar

~$ ls -al /usr/share/Kernow/lib/saxon9-dom.jar
-rw-r--r-- 1 root root 129212 2010-01-31 21:06 /usr/share/Kernow/lib/saxon9-dom.jar

~$ echo $CLASSPATH
/usr/share/Kernow/lib/saxon9-dom.jar

~$ 
```

---

### Post by dilantha on 2011-01-12
Hi All,

I followed the steps and set the the path correctly. this is my environment file

```

PATH="/usr/lib/jvm/java-6-sun-1.6.0.22/bin:.:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games"
JAVA_HOME="/usr/lib/jvm/java-6-sun-1.6.0.22"
CLASSPATH="/usr/lib/jvm/java-6-sun-1.6.0.22/lib:."

```but im getting an error when im trying to run a simple java programme even. for example if i run the program using 
```

java test
```it gives me

```
Exception in thread "main" java.lang.NoClassDefFoundError: test
```but if i run it using

```
java -classpath . test
```then it runs properly. can any one help me with this ? Thanks in advance.

---

### Post by cwbr on 2011-05-16
I'm pretty sure that the problem with that is the ":." at the end of the CLASSPATH. I removed it from mine and everything worked fine.
If anyone wants to tell me why some people have this and do not seem to have a problem, I would be interested to know. Also, what does the ":." addition do?

---

### Post by r-senior on 2011-05-16
You don't need to set JAVA_HOME and CLASSPATH to program in Java.

For example:

```

$ echo $JAVA_HOME

$ echo $CLASSPATH

$ vi Test.java
$ cat Test.java
public class Test {
	public static void main(String ... args) {
		System.out.println("Hello World");
	}
}
$ javac Test.java
$ java Test
Hello World

```

Read this carefully to understand why PATH does not need to be set for Java - in fact why it *should not* be set:

```

$ which java
/usr/bin/java
$ ls -l /usr/bin/java
lrwxrwxrwx 1 root root 22 2011-04-08 15:30 /usr/bin/java -> /etc/alternatives/java
$ ls -l /etc/alternatives/java
lrwxrwxrwx 1 root root 36 2011-04-08 15:30 /etc/alternatives/java -> /usr/lib/jvm/java-6-sun/jre/bin/java

```

When it comes to using other libraries, it is much better to specify them on the command line or in a script/build tool rather than in a machine specific configuration. If there are too many, you should be using a build tool like Maven or an IDE (preferably an IDE that supports Maven builds ;)).

If you use an IDE without Maven, .jar files usually get added to the classpath as "libraries" for the project. It's just locating the .jar file and adding that location to the -classpath option.

If you use Maven, Maven takes care of your library dependencies (and their dependencies (and their dependencies ...)).

---

### Post by ishan_sangai on 2011-09-21
hey, 

Thanks
 It helped me. Now I can see classpath with echo $CLASSPATH.

regards,
Ishan

---

