---
title: "[SOLVED] Java 3D Installation"
date: 2008-02-07
forum: Programming Talk
---

### Post by okey666 on 2008-02-07
I am having trouble installing Java 3D. I attempt to install it using the binaries or zips available on [https://java3d.dev.java.net/](https://java3d.dev.java.net/) but whenever I try to compile it cant find it, it says:
1. ERROR in Hello3d.java (at line 1)
        import com.sun.j3d.utils.universe.SimpleUniverse;
                   ^^^
The import com cannot be resolved
 ...and so on.

I am pretty much a beginner in Java working from the book, Killer Game Programming in Java. I use Gutsy 86x and have installed Java 6 using Synaptic. I can compile standard programs it is just the 3D causing problems. Please could someone help!

---

### Post by hod139 on 2008-02-07
Why don't you use one of their installers?  If you don't want to, did you follow the directions on their site: [http://download.java.net/media/java3d/builds/release/1.5.1/README-download.html](http://download.java.net/media/java3d/builds/release/1.5.1/README-download.html)

---

### Post by okey666 on 2008-02-08
It still gives the same errors.

---

### Post by hod139 on 2008-02-08
What gives the same errors, their installer or the manual method?

What's the output of:
```

java -version

```
and
```
javac -version
```

---

### Post by Shin_Gouki2501 on 2008-02-08
use eclipse.. u need to include the java3d libarys to ur hello world project/ buildpath
Then compile again and it should work.
btw. java is pretty amazing just tried &quot;lobo Browser&quot; which im currently using to write this.
No install just run. I like that :D

---

### Post by okey666 on 2008-02-08
The first one gives:
oscar@oscar-desktop:~/Desktop$ java -version
java version "1.6.0_03"
Java(TM) SE Runtime Environment (build 1.6.0_03-b05)
Java HotSpot(TM) Server VM (build 1.6.0_03-b05, mixed mode)

and the second:
oscar@oscar-desktop:~/Desktop$ javac -version
Eclipse Java Compiler v_774_R33x, 3.3.1, Copyright IBM Corp 2000, 2007. All rights reserved.

Like I said everything is fine until I try to compile any Java 3D programs then it says it can't find anything to do with Java 3D.

---

### Post by okey666 on 2008-02-08
I will try Eclipse.

---

### Post by hod139 on 2008-02-08
> **okey666 said:**
> The first one gives:
oscar@oscar-desktop:~/Desktop$ java -version
java version "1.6.0_03"
Java(TM) SE Runtime Environment (build 1.6.0_03-b05)
Java HotSpot(TM) Server VM (build 1.6.0_03-b05, mixed mode)

and the second:
oscar@oscar-desktop:~/Desktop$ javac -version
Eclipse Java Compiler v_774_R33x, 3.3.1, Copyright IBM Corp 2000, 2007. All rights reserved.

Looks like one problem is that you have a mismatch between your compiler and runtime.  Try running 
```

sudo update-java-alternatives -s java-6-sun

```

---

### Post by okey666 on 2008-02-08
Fixed that problem. Thanks so much I have been trying for AGES. Now all I have to do is hope it runs!

---

### Post by okey666 on 2008-02-08
That worked too. Great, thanks everyone for quick replys.

---

### Post by danicyber on 2010-02-17
Unfortunately these past posts didn't help in my case.
Trying to have Java3D to work for imageJ
1. downloaded j3d-jre.zip and unziped in mypath/
2. set environment variables as instructed in the installation readme file
3. downloaded Install_Java3D.jar and put in the imageJ plugin folder
4. run imagej as sudo and ran Install_Java3D.jar, which asked for  j3d-jre.zip
5. imageJ prompts successful installation 
6. java3D continues not be accessible/visible in imageJ
7. closed and opened imageJ
8. java3D continues not be accessible/visible in imageJ

I'm using:
Linux Ubuntu Jaunty 9.04
java version "1.6.0_0"
OpenJDK Runtime Environment (IcedTea6 1.4.1) (6b14-1.4.1-0ubuntu12)
OpenJDK 64-Bit Server VM (build 14.0-b08, mixed mode)
javac 1.6.0_0

---

