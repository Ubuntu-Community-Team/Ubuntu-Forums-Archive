---
title: "Java JDK and JRE free or open"
date: 2006-11-14
forum: Programming Talk
---

### Post by jae1227 on 2006-11-14
Is jdk source code released? See when you go to sun's page they have binary jdk for windows, Linux and solaris. And these were only for x86 class processors so i thought how does apple have a jdk for thier os. Is the source available and they just compiled it for ppc. Well then when i installed Ubuntu on my ibook i found i could not install the jdk from sun. But Linux includes gcj (GNU Compiler for Java) just like the javac command in jdk but gcj only supported up to 1.4.2 not 1.5.9 . MY conclusion is that is was close source so did gcj reverse engineer it. Now in my hunt for jdk 1.5 for ppc Linux i found IBM made one for ppc and that is what i am using now. So did people like Apple and IBM buy the rights to the code from Sun and is this why there are so many Java Virtual Machines? Hope someone help me understand why there are some many jvm from so many different companies and why so many. There is just one company that makes the FLash 9 player and that is Adobe and gnu must reverse engineer it to make a flash player for it. Thanks a lot O and i did see java went open source what ever that changes. Now it is under the GPLv2 but how has that changed.

---

### Post by igknighted on 2006-11-15
Java is being released under the GPL in March '07 I believe, although the source code for a lot of it is available at java.sun.com already

---

### Post by shining on 2006-11-15
I'm not sure if I understood everything correctly (probably not), but well..
I believe the whole JDK source is available, but under a restrictive license, which is not considered open source. I think redistribution isn't even possible, since you need to register first for downloading it:
[http://java.sun.com/j2se/jrl_download.html](http://java.sun.com/j2se/jrl_download.html)

And about what is now really open source (under the GPL), it's there:
[http://www.sun.com/software/opensource/java/faq.jsp](http://www.sun.com/software/opensource/java/faq.jsp)

> 
 
Q:
What components of the JDK software are you open sourcing today?
A:
We're open sourcing the Java programming language compiler ("javac"), and the Java HotSpot virtual machine. In addition, we're open sourcing the JavaHelp 2.0 extensible help system, Sun's reference implementation of JSR 97 in this first code release. The JavaHelp code base is found at [https://javahelp.dev.java.net](https://javahelp.dev.java.net).

Q:
Is the JDK source code under the GPL as well?
A:
Yes, the JDK is licensed under the GPL version 2 with the Classpath exception. This license, which will be used for all of Sun's Java implementations, is endorsed by the Free Software Foundation, and is the license used by the GNU/Linux operating system.
 
Q:
When will you finish open sourcing the JDK? What is the timeline?
A:
We expect to release a fully buildable JDK based almost completely on open-sourced code in the first half of 2007.



There is just one thing I'm not sure, by Classpath, they mean the whole API, right?
Because, now, you've the java executable (the Java Virtual Machine) under the GPL, and the javac executable too (java compiler), but the API is not available.
So, I think that's what they will provide in the first half of 2007, the whole API under an open source license (maybe not the GPL), but I'm not sure about that.

---

### Post by shining on 2006-11-15
Ah, no.
By "GPL version 2 with the Classpath exception", I believe they refer to the license used by GNU Classpath, which is the GPL with a special exception:
[http://www.gnu.org/software/classpath/license.html](http://www.gnu.org/software/classpath/license.html)

So apparently, the JDK is open source, under the GPL with an exception, but it's just not available today, and it'll be in 2007.

---

### Post by FyreBrand on 2006-11-15
Some parts have been opened.  Like you said, the compiler and the virtual machine are already there.  I think they are waiting to release the JDK in spring to coincide with a new version release.

Licensing and the exceptions have always been a little confusing to me.  I think the classpath exception means that the code is opened and licensed under GPL2 but if a business wants to pay for a proprietary license they can and still keep their source closed.  I probably have it all wrong, but that's what I could get out of it.

---

### Post by kuja on 2006-11-15
As per the class path exception deal, from what I gathered, means that proprietary applications can still use the gpl'd java without having to gpl their code.

---

### Post by shining on 2006-11-15
> **kuja said:**
> As per the class path exception deal, from what I gathered, means that proprietary applications can still use the gpl'd java without having to gpl their code.

Yes, that's what I understood also. But I think saying "any applications that doesn't have a gpl compatible license" would be more accurate than "proprietary applications".
So this classpath exception looks quite necessary :)

---

### Post by _asc_ on 2006-11-16
As mentioned in some of the previous posts, the JDK will be open sourced under the GPL V2 with the classpath exception in the first half of 2007. AFAIK, they are planning to release it in March 2007. The reason why they did not do it now is that not all the code in the JDK is owned by Sun. This is especially true for the Java2D API (rasterizers, etc.). Currently they are talking to the owners of that code to evaluate if they agree to open source these parts or if Sun has to replace it with their own implementation or maybe an implemantation from GNU Classpath. If they do not manage to sort these issues out in time, they might aim for an interim solution by open sourcing all the code of the JDK that is owned by SUN and providing a couple of binary modules for the code that is not owned by them, until they are able to replace these code parts. Eventually, all parts of Java will be GPLed.

And yes, the sole reason for the classpath exception is that developers using the JDK are not forced to open source their code.

---

