---
title: "Having major trouble getting a HelloWorld program running with JOGL!"
date: 2011-07-09
forum: Programming Talk
---

### Post by s3a on 2011-07-09
I believe the following will be self-explanatory:

```

ubuntu@ubuntu:/tmp$ echo $CLASSPATH
/.:/usr/share/java/jogl-1.1.1+dak1.jar:/usr/share/java/gluegen-rt-1.1.1+dak1.jar:/usr/share/java/jogl.jar:/usr/share/java/gluegen-rt.jar
ubuntu@ubuntu:/tmp$ apt-cache policy libjogl-java;dpkg -L libjogl-java
libjogl-java:
  Installed: 1.1.1+dak1-8
  Candidate: 1.1.1+dak1-8
  Version table:
 *** 1.1.1+dak1-8 0
        500 http://archive.ubuntu.com/ubuntu/ lucid/universe Packages
        100 /var/lib/dpkg/status
/.
/usr
/usr/share
/usr/share/java
/usr/share/java/jogl-1.1.1+dak1.jar
/usr/share/java/gluegen-rt-1.1.1+dak1.jar
/usr/share/doc
/usr/share/doc/libjogl-java
/usr/share/doc/libjogl-java/README.Debian
/usr/share/doc/libjogl-java/copyright
/usr/share/doc/libjogl-java/changelog.Debian.gz
/usr/share/java/jogl.jar
/usr/share/java/gluegen-rt.jar
ubuntu@ubuntu:/tmp$ cat HelloWorld.java 
import net.java.games.jogl.*;

public class HelloWorld {
  public static void main (String args[]) {
    try {
      System.loadLibrary("jogl");
      System.out.println("Hello World! (The native libraries are installed.)");
      GLCapabilities caps = new GLCapabilities();
      System.out.println("Hello JOGL! (The jar appears to be available.)");
    } catch (Exception e) {
      System.out.println(e);
    }
  }
}
ubuntu@ubuntu:/tmp$ javac HelloWorld.java 
HelloWorld.java:1: package net.java.games.jogl does not exist
import net.java.games.jogl.*;
^
HelloWorld.java:8: cannot find symbol
symbol  : class GLCapabilities
location: class HelloWorld
      GLCapabilities caps = new GLCapabilities();
      ^
HelloWorld.java:8: cannot find symbol
symbol  : class GLCapabilities
location: class HelloWorld
      GLCapabilities caps = new GLCapabilities();
                                ^
3 errors
ubuntu@ubuntu:/tmp$ lsb_release -a;uname -a
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 10.04.2 LTS
Release:	10.04
Codename:	lucid
Linux ubuntu 2.6.32-28-generic #55-Ubuntu SMP Mon Jan 10 23:42:43 UTC 2011 x86_64 GNU/Linux
ubuntu@ubuntu:/tmp$

```

I remember a few Googles ago, someone said that that package is deprecated or something of the sort but I had tried it to no success.

If more information is needed, just ask.

Any help getting this to work would be greatly appreciated!
Thanks in advance!

P.S.
This is not an Ubuntu-specific issue either. I am having the same issue on Debian systems, as well; although I do think that it is me doing something wrong.

---

### Post by PaulM1985 on 2011-07-09
I would recommend using lwjgl.  I had trouble with JOGL not working on some systems.

Paul

EDIT: I did make a suggestion for fixing the problem, but after further googling I realised I was wrong... sorry

---

### Post by PaulM1985 on 2011-07-09
Have you got the native jogl libs?

Does this tutoriol help?
[http://www.cs.umd.edu/~meesh/kmconroy/JOGLTutorial/](http://www.cs.umd.edu/~meesh/kmconroy/JOGLTutorial/)

Paul

---

