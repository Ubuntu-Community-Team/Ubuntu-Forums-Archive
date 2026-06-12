---
title: "Eclipse JME errors access restriction"
date: 2007-10-06
forum: Programming Talk
---

### Post by draenox on 2007-10-06
Hello all,

I am having trouble compiling the JMonkey Engine in eclipse. I keep getting access restriction errors. For some reason, my system cannot access a certain java file.

> Access restriction: The constructor BASE64Decoder() is not accessible due to restriction on required library /usr/lib/jvm/java-6-sun-1.6.0.00/jre/lib/rt.jar

That is the first of 11 similar errors. I am not sure if I went about the right way of doing this, but I tried 

>  sudo chmod u=rx /usr/lib/jvm/java-6-sun-1.6.0.00/jre/lib/rt.jar

to give myself read and execute permission on that jar file, but I still get the 11 errors after I compile again. Has anyone else encountered this error or have an idea of what to do to solve the access restrictions?

Thanks for reading.

---

### Post by Oberiko on 2008-08-25
I had this error as well.

According to the [M2Eclipse FAQ]("http://docs.codehaus.org/display/M2ECLIPSE/Project+FAQ"), we can safely ignore them.  The exact wording is as follows:

> **_Compilation errors on restricted classes_**

Projects using classes from rt.jar, such as com.sun.* (and some others) can have compilation errors like: "Access restriction: The type RE is not accessible due to restriction on required library <jre_path>/lib/rt.jar". Such errors indicate use of non-API classes and those access rules are defined by Eclipse JDT.

You can change compiler settings to not fail on those restrictions in workspace settings in Window \/ Preferences \/ Java \/ Compiler \/ Errors/Warnings \/ Deprecated and restricted API \/ Forbidden reference (access rules) \/ Warnings; or per-project from Project \/ Properties \/ Java Compiler \/ Errors\/Warnings \/ Deprecated and restricted API \/ Forbidden reference (access rules) \/ Warnings

---

### Post by Matt-L on 2009-07-07
> **Oberiko said:**
> I had this error as well.

According to the [M2Eclipse FAQ]("http://docs.codehaus.org/display/M2ECLIPSE/Project+FAQ"), we can safely ignore them.  The exact wording is as follows:
That may work; instead, what I actually did was go to Eclipse's preferences, Installed JREs section, and add the path to Sun's JDK that I had installed, /usr/lib/jvm/java-6-sun-1.6.0.13 -- Previously, the JRE that was selected was OpenJDK6. With the Sun one, the errors went away. (I had to change the JRE System Library for the project's Build Path as described in a previous post.)

Cheers.

---

### Post by imtheguru on 2009-11-20
> **Matt-L said:**
> That may work; instead, what I actually did was go to Eclipse's preferences, Installed JREs section, and add the path to Sun's JDK that I had installed, /usr/lib/jvm/java-6-sun-1.6.0.13 -- Previously, the JRE that was selected was OpenJDK6. With the Sun one, the errors went away. (I had to change the JRE System Library for the project's Build Path as described in a previous post.)

Cheers.May work? The solution in Oberiko's post will ALWAYS work with SUN-JRE (or JDK); there is no ambiguity.

The cause for the ERROR is attempting to access internal SUN API directly without going to the appropriate higher level handlers.

If you simply must use internal API, reduce the priority of the checks in Eclipse as described in Oberiko's post.

---

