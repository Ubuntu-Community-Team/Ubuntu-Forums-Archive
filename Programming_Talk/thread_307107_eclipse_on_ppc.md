---
title: "eclipse on ppc?"
date: 2006-11-26
forum: Programming Talk
---

### Post by davidmaxwaterman on 2006-11-26
Does anyone have Eclipse running on PPC?

I installed it, but it won't run :

"A Java Runtime Environment (JRE) or Java Development Kit (JDK) must be available in order to run Eclipse. No Java virtual machine was found after searching the following locations:
/usr/lib/j2sdk1.4-sun/bin/java
"

Not surprising :

$ ls /usr/lib/j2sdk1.4-sun/bin/java
ls: /usr/lib/j2sdk1.4-sun/bin/java: No such file or directory

However :

"
s$ java
Usage: gij [OPTION] ... CLASS [ARGS] ...
          to invoke CLASS.main, or
       gij -jar [OPTION] ... JARFILE [ARGS] ...
          to execute a jar file
Try `gij --help' for more information.
"

So, I think Java is installed.

I looked at other threads and they talk about Sun's Java, but I looked on their web site and it only seems to support ia32 and x86_64 - not ppc.

I want to Eclipse out for Nokia/Symbian development in C++.

Anyone help me?

Max.

---

### Post by shining on 2006-11-26
How did you install eclipse?
Do you have a /etc/eclipse/java_home file?
Which directories do you have in /usr/lib/jvm/?
If you have a /etc/eclipse/java_home file and a /usr/lib/jvm/java-gcj directory, then add it at the top of the java_home file.

---

### Post by davidmaxwaterman on 2006-11-26
Thanks for helping :)

> **shining said:**
> How did you install eclipse?


Using synaptic.

> **shining said:**
> 
Do you have a /etc/eclipse/java_home file?


Yes.

$ ls -l /etc/eclipse/
total 4
-rw-r--r-- 1 root root 411 2006-10-23 18:32 java_home


> **shining said:**
> 
Which directories do you have in /usr/lib/jvm/?


Er, none :$ :

$ ls -l /usr/lib/jvm/
ls: /usr/lib/jvm/: No such file or directory


> **shining said:**
> 
If you have a /etc/eclipse/java_home file and a /usr/lib/jvm/java-gcj directory, then add it at the top of the java_home file.

So, since I don't have the /usr/lib/jvm/ directory, what do I do?

Max.

---

### Post by shining on 2006-11-27
Do you have java-gcj-compat installed?
According to this page:
[http://packages.ubuntu.com/cgi-bin/search_contents.pl?searchmode=filelist&word=java-gcj-compat&version=edgy&arch=powerpc](http://packages.ubuntu.com/cgi-bin/search_contents.pl?searchmode=filelist&word=java-gcj-compat&version=edgy&arch=powerpc)

It should provide a jvm in /usr/lib/jvm/java-gcj

This shouldn't be required though, I just installed eclipse deb package, and it installed the required dependencies for me.

---

### Post by davidmaxwaterman on 2006-11-27
> **shining said:**
> Do you have java-gcj-compat installed?
According to this page:
[http://packages.ubuntu.com/cgi-bin/search_contents.pl?searchmode=filelist&word=java-gcj-compat&version=edgy&arch=powerpc](http://packages.ubuntu.com/cgi-bin/search_contents.pl?searchmode=filelist&word=java-gcj-compat&version=edgy&arch=powerpc)

It should provide a jvm in /usr/lib/jvm/java-gcj

This shouldn't be required though, I just installed eclipse deb package, and it installed the required dependencies for me.

Haha! I installed that, and it just worked :D

Thanks!

Max.

---

### Post by Ramses de Norre on 2006-11-27
Eclipse runs a lot more stable in sun's java here, just to let you know ;)

---

### Post by shining on 2006-11-27
> **Ramses de Norre said:**
> Eclipse runs a lot more stable in sun's java here, just to let you know ;)

I didn't see any differences in stability.
However, out of the box, eclipse is incredibly faster using sun's java compared to gcj.
But not so much after installing the eclipse-gcj package. (Or several eclipse-*-gcj packages if you don't have the eclipse-gcj metapackage).
This makes a HUGE difference.

---

### Post by davidmaxwaterman on 2006-11-27
> **Ramses de Norre said:**
> Eclipse runs a lot more stable in sun's java here, just to let you know ;)

I read that, yes. However, I have yet to find a version of Sun's Java for PPC...links welcome.

---

### Post by techrush on 2006-11-27
sun's java is not available on ppc at the moment. however ibm does have its own java jdk that i use on my ppc ubuntu install as a browser plugin and also to run java apps such as azureus. it performs much better than gcj imo

---

### Post by davidmaxwaterman on 2006-11-29
> **davidmaxwaterman said:**
> Haha! I installed that, and it just worked :D

Thanks!

Max.

Ah. It was a permissions denied problem - I had to do it all as root. Curious.

---

