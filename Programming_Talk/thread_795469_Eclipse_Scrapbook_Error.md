---
title: "Eclipse Scrapbook Error"
date: 2008-05-15
forum: Programming Talk
---

### Post by mscxx on 2008-05-15
When using scrapbook in eclipse with Ubuntu 8.04 I'm getting this error whenever I try to evaluate a statement.

I googled it and one other person has had the same problem, but there was no solution.

Error:
org.eclipse.debug.core.DebugException: Evaluation failed - unable to instantiate code snippet class.
	at org.eclipse.jdt.internal.debug.eval.LocalEvaluationEngine.newInstance(LocalEvaluationEngine.java:1008)
	at org.eclipse.jdt.internal.debug.eval.LocalEvaluationEngine.run(LocalEvaluationEngine.java:228)
	at org.eclipse.jdt.internal.debug.core.model.JDIThread.runEvaluation(JDIThread.java:584)
	at org.eclipse.jdt.internal.debug.eval.LocalEvaluationEngine.acceptClassFiles(LocalEvaluationEngine.java:217)
	at org.eclipse.jdt.internal.core.eval.RequestorWrapper.acceptClassFiles(RequestorWrapper.java:47)
	at org.eclipse.jdt.internal.eval.EvaluationContext.evaluate(EvaluationContext.java:245)
	at org.eclipse.jdt.internal.eval.EvaluationContext.evaluate(EvaluationContext.java:263)
	at org.eclipse.jdt.internal.core.eval.EvaluationContextWrapper.evaluateCodeSnippet(EvaluationContextWrapper.java:237)
	at org.eclipse.jdt.internal.debug.eval.LocalEvaluationEngine$1.run(LocalEvaluationEngine.java:428)
	at java.lang.Thread.run(Thread.java:619)

Does anyone have an idea as to what could be causing this?:confused:

---

### Post by mscxx on 2008-05-15
oh! I figured it out. There must have been an error when creating the workspace, because it was missing a file needed to evaluate expressions.

So I created another workspace and it is now working perfectly.

---

### Post by potzdonner on 2008-10-23
> **mscxx said:**
> oh! I figured it out. There must have been an error when creating the workspace, because it was missing a file needed to evaluate expressions.

So I created another workspace and it is now working perfectly.

Hallo everybody

I got the same problem with the exactly same error messages unter Eclipse 3.2.2

I fixed the problem like following: right click the scrapbook-file in the package explorer and than changed the runtime jre, preferably to one installed on your machine :)

[http://javapup.i-networx.de/MyScrapbook.jpg]("http://javapup.i-networx.de/MyScrapbook.jpg")

Bye
Giuso

---

### Post by bgryderclock on 2008-12-13
I had the same error. I tried the fixes mentioned above with no success.

This worked for me: _**[COLOR="Blue"][https://help.ubuntu.com/community/EclipseIDE](https://help.ubuntu.com/community/EclipseIDE)[/COLOR]**_


> 
[B]sudo apt-get install openjdk-6-jdk

gksudo gedit /etc/eclipse/java_home[/B]

Now, on a line right before /usr/lib/jvm/java-gcj, type the following:

**/usr/lib/jvm/java-6-openjdk**

The file should now look like this:

[B]# This file determines the search order the Eclipse Platform uses to find a
# compatible JAVA_HOME. This setting may be overridden on a per-user basis by
# altering the JAVA_HOME setting in ~/.eclipse/eclipserc.

#/usr/lib/jvm/java-7-icedtea
/usr/lib/jvm/java-6-openjdk
/usr/lib/jvm/java-gcj
...[/B]

[SIZE="4"]Eclipse and Sun Java
[/SIZE]

To install the Sun Microsystems JDK, install the sun-java6-jdk package from the multiverse repository.

By default, the Eclipse which is packaged with Ubuntu runs with the GCJ JVM and not the JVM supplied by Sun Microsystems even if you have installed the Sun Microsystems version.

Note: If you're using Ubuntu 6.06 (Dapper) you'll need to install sun-java6-jdk from the dapper-backports Multiverse repository. Please take a look at UbuntuBackports for more information on using backport repositories.

In order to load eclipse with the Sun JVM, edit the /etc/eclipse/java_home file.

    * Add the path of the Sun JVM above the GCJ JVM entry. 

[B]/usr/lib/jvm/java-6-sun
/usr/lib/jvm/java-gcj
  [...][/B]

    *

      To ensure that the change has happened, open Eclipse and click on Help -> About Eclipse SDK -> Configuration details and look for this line: 

[B]  [...]
-vm
/usr/lib/jvm/java-6-sun/bin/java
  [...][/B]

As an added bonus, you may also enjoy a speed gain after doing this.

Sun JVM System Wide

You may also want to use the Sun JVM system-wide. Enabling the Sun JVM is a snap using update-java-alternatives.

    * First, find out which versions of Java you have installed through Ubuntu. 

[B]sudo update-java-alternatives --list

output:

   java-1.5.0-sun 53 /usr/lib/jvm/java-1.5.0-sun
   java-6-sun 63 /usr/lib/jvm/java-6-sun[/B]

    * Next, specify the one you would like as the default. 

**sudo update-java-alternatives --set java-6-sun**

Note: The JVMs listed may differ depending on the version of Ubuntu you're using and the setup of your system. The important thing is to choose the JVM with **sun** in the title.

---

