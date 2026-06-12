---
title: "Java 6 Update 2"
date: 2007-07-06
forum: Programming Talk
---

### Post by brodock on 2007-07-06
When it will arrive at our feisty fawn repository?
They did a lot of improvements, like performance and the one i most like is the look and feel on linux, works better now

---

### Post by bluehue on 2007-07-06
Was the first update released on the repositories? I searched and couldn't find it. Or maybe I already have the first update installed?
```

spiral@spiral-desktop:~$ java -version
java version "1.6.0"
Java(TM) SE Runtime Environment (build 1.6.0-b105)
Java HotSpot(TM) Client VM (build 1.6.0-b105, mixed mode, sharing)
``` :confused:

---

### Post by vcardona on 2007-07-06
I haven't seen the first update yet in the repository.  I might have missed it.  I am new to Ubuntu.  However if that isn't in there then I doubt we will see 1.6.0_02 anytime soon.

---

### Post by kknd on 2007-07-06
I dont think that an updated version will arive in the repos. Since 6.1 I install manually.

---

### Post by samjh on 2007-07-06
The one in Ubuntu 7.04 is still 1.6.0.00, I believe.

Just posted this in the repos forum: [http://ubuntuforums.org/showthread.php?p=2976653#post2976653](http://ubuntuforums.org/showthread.php?p=2976653#post2976653)

---

### Post by growltiger on 2007-07-19
If I use the multiverse package I get build 1.6.0-b105.  So I am still mired in the FCS version of Java 6.

I tried using java-packages (#28) to hack in jdk 6u2 but it does not support it.  I get the error message about a missing plugin.  I suspect that the real problem is a name pattern mismatch.  I really do *not* want to be bothered with the trial and error of hacking an acceptable pattern so I suppose it is back to the tedium of setting environment classpaths when I need one JDK over the other.

Is there a clean solution out there?

---

### Post by growltiger on 2007-07-19
I found that if I took rev 31 of java-packages (found here: <https://launchpad.net/ubuntu/gutsy/+source/java-package/0.31>, I could install Java 6u2.

---

### Post by Gremlinzzz on 2007-07-19
> **growltiger said:**
> I found that if I took rev 31 of java-packages (found here: <https://launchpad.net/ubuntu/gutsy/+source/java-package/0.31>, I could install Java 6u2.

uh yeah i have a response WHAT!

---

### Post by Gremlinzzz on 2007-07-19
ok download jre-6u2-linux-i586.bin did
cd Desktop
/Desktop$ sudo chmod a+x jre-6u2-linux-i586.bin
/Desktop$ ./jre-6u2-linux-i586.bin
got a positive response clicked more and type in yes said done but i don't see the update when i java -version
i updated list    update-java-alternatives -l
select your preference from the list
 sudo update-alternatives --config java
nothing new on the list
still have Java(TM) SE Runtime Environment (build 1.6.0-b105)
Java HotSpot(TM) Client VM (build 1.6.0-b105, mixed mode, sharing)
where did the update go?

---

### Post by S1l3nt_Hunt3r on 2007-07-20
> **Gremlinzzz said:**
> ok download jre-6u2-linux-i586.bin did
cd Desktop
/Desktop$ sudo chmod a+x jre-6u2-linux-i586.bin
/Desktop$ ./jre-6u2-linux-i586.bin
got a positive response clicked more and type in yes said done but i don't see the update when i java -version
i updated list    update-java-alternatives -l
select your preference from the list
 sudo update-alternatives --config java
nothing new on the list
still have Java(TM) SE Runtime Environment (build 1.6.0-b105)
Java HotSpot(TM) Client VM (build 1.6.0-b105, mixed mode, sharing)
where did the update go?

I did the process almost like you, (copied the bin file to a different folder and run the file with sudo). The install process made a new folder in the same folder where I put the bin file. 

But it's not working either.

I compared the new folder with /usr/lib/jvm/java-6-sun-1.6.0.00/ and they are different. But inside the java-6-sun-1.6.0.00 there is a folder  (jre) which have  the same names of the files  and folders than the new folder

are jvm and jre the same thing? :confused:

---

### Post by Gremlinzzz on 2007-07-21
going uninstall and follow these directions 
[http://java.sun.com/javase/6/webnotes/install/jre/install-linux.html#self-extracting](http://java.sun.com/javase/6/webnotes/install/jre/install-linux.html#self-extracting)
be back with update
:guitar:

---

### Post by Gremlinzzz on 2007-07-21
Forget it anyone have a java update deb package
:lolflag:

---

### Post by Gremlinzzz on 2007-07-21
Better yet put this
[http://java.sun.com/javase/6/webnotes/install/jre/install-linux.html#self-extracting](http://java.sun.com/javase/6/webnotes/install/jre/install-linux.html#self-extracting)
in noobe paste able language
:guitar:

.

---

### Post by Gremlinzzz on 2007-07-21
> **Gremlinzzz said:**
> Better yet put this
[http://java.sun.com/javase/6/webnotes/install/jre/install-linux.html#self-extracting](http://java.sun.com/javase/6/webnotes/install/jre/install-linux.html#self-extracting)
in noobe paste able language
:guitar:

.

forgot    	jre-6u2-linux-i586.bin
[https://sdlc5b.sun.com/ECom/EComActionServlet/DownloadPage:~:com.sun.sunit.sdlc.content.DownloadPageInfo;jsessionid=E8A2631719BBB6092F5594CD5090D9A0;jsessionid=E8A2631719BBB6092F5594CD5090D9A0](https://sdlc5b.sun.com/ECom/EComActionServlet/DownloadPage:~:com.sun.sunit.sdlc.content.DownloadPageInfo;jsessionid=E8A2631719BBB6092F5594CD5090D9A0;jsessionid=E8A2631719BBB6092F5594CD5090D9A0)

---

### Post by Squid_blk on 2007-08-24
I need JRE 6.0 Update to run an updated application I used to use.  I have 6.0 but when I did what S1l3nt_Hunt3r did, I got a new folder with another version of JRE and the system only recognized the older one.  It would be nice if the software would say hey there is an update would you like to install it. But it apparently does not.  What do I have to do, uninstall the old one?  I am new to Linux and I have no idea even where the old one resides.  I know the version I have works but will not work with what I want it to do.  Also I have no idea on how to update the Firefox plugin.  All I know is that the instructions on Java's site do not seem to work and if I could read German a previous instruction link submitted in this thread might have been helpful but, not.

---

