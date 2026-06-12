---
title: "Problems with Java/Eclipse"
date: 2006-06-07
forum: Programming Talk
---

### Post by Amablue on 2006-06-07
I'm not quite sure which one is at fault, but here's what's happening. 

I'm trying to make an ArrayList, but the the compiler keeps complaining with this error:```
The type ArrayList is not generic; it cannot be parameterized with 
 arguments <String>
```
Someone on another message board suggested that I might not have the correct version of Java. It seems I was still using 1.4, so I went to Synaptic and installed the sun-java5-jdk (and whatever else came with it). Then I opened up a terminal and set the default java version to 5.0 with this:
```
sudo update-alternatives --config java
```
Also, eclipse's default compliance level is set to 5.0. I'm still getting the same errors though, and I desperatly need these ArrayLists to work for my little project.

---

### Post by mlind on 2006-06-07
Generics is feature of java 1.5, you can hint List interface and its implementation for what
kind of objects they'll contain. It's typesafe and preferred way.

Eclipse should mark it as warning by default, but not error. You can change compiler
compilance level to 1.4 if you're annoyed by these warnings. If those are really reported
as errors, check from Preferences > Java > Compiler > Errors/Warnings >
Generic types > Unchecked Generic Type Operation    is set to 'Warning'


/edit
If no avail, check using
```

update-alternatives --display java
update-alternatives --display javac

```

that those point to Sun's java and javac accordingly. Sometimes setting 
JAVA_HOME environment variable helps, but Eclipse does work without it.

---

### Post by obiyoda on 2006-06-07
Eclipse in dapper seems to depend on the gij java environmnet which is java 1.4 compliant.  If you do a java -version in a terminal it should let you know if you are indeed using that version.

---

### Post by mlind on 2006-06-07
You can also change the default JRE to another from Eclipse's Preferences, but I
don't know if it actually resolves this problem.

---

### Post by hod139 on 2006-06-07
[quote=Amablue]... It seems I was still using 1.4, so I went to Synaptic and installed the sun-java5-jdk (and whatever else came with it). Then I opened up a terminal and set the default java version to 5.0 with this:
```
sudo update-alternatives --config java
``` 
[/quote] 
This isn't quite enough to get eclipse fully utilizing Sun's Java.  I wrote an [earlier post]("http://ubuntuforums.org/showpost.php?p=1065271&postcount=8") about howto setup Sun's Java and eclipse.  Eclipse tends to ignore Ubuntu's java_home settings.

> 
Also, eclipse's default compliance level is set to 5.0. I'm still getting the same errors though, and I desperatly need these ArrayLists to work for my little project.
Projects can override the default compliance levels.  Make sure your project specific settings are using compliance level 5.0.  
Project --> Properties
Select Java Compiler in the left Window and verify the compliance level for that project.

Also make sure under 
Window-->Preferences-->Java-->Installed JREs, Sun's java-1.5 is listed and checked as the default.

Hope that helps

---

### Post by jvictor on 2006-06-10
> Projects can override the default compliance levels. Make sure your project specific settings are using compliance level 5.0.
Project --> Properties
Select Java Compiler in the left Window and verify the compliance level for that project.

This can be the cause , bcz eclipse has project specific settings

---

