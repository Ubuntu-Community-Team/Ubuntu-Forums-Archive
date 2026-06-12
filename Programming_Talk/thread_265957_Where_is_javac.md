---
title: "Where is javac?"
date: 2006-09-26
forum: Programming Talk
---

### Post by Seantiago on 2006-09-26
I was recently having problems getting java files to compile.  Turns out I had neglected to install the JDK.  Woulda thought that comes standard, but whatevs.  So I use Synaptic to download and install JDK 1.5.0-6 and all the things that come with it (sun-java5-bin, sun-java5-demo, and sun-java5-jre all come along with sun-java5-jdk).

That works OK, and now, awesomely, the javac command works!

But I seem to have a bigger problem on my hand.  When I try to *run* the damn thing, I get this big-assed message:

```
Exception in thread "main" java.lang.UnsupportedClassVersionError: HelloWorld (Unsupported major.minor version 49.0)
        at java.lang.ClassLoader.defineClass0(Native Method)
        at java.lang.ClassLoader.defineClass(ClassLoader.java:539)
        at java.security.SecureClassLoader.defineClass(SecureClassLoader.java:123)
        at java.net.URLClassLoader.defineClass(URLClassLoader.java:251)
        at java.net.URLClassLoader.access$100(URLClassLoader.java:55)
        at java.net.URLClassLoader$1.run(URLClassLoader.java:194)
        at java.security.AccessController.doPrivileged(Native Method)
        at java.net.URLClassLoader.findClass(URLClassLoader.java:187)
        at java.lang.ClassLoader.loadClass(ClassLoader.java:289)
        at sun.misc.Launcher$AppClassLoader.loadClass(Launcher.java:274)
        at java.lang.ClassLoader.loadClass(ClassLoader.java:235)
        at java.lang.ClassLoader.loadClassInternal(ClassLoader.java:302)

```

Yikes.  Something's unhappy, and I dunno what to do.  Any suggestions?

By the way, this is the file I'm trying to run:

```
public class HelloWorld
{
    static public void main(String[] args)
    {
	System.out.println("Hello World!");
    }
}

```

---

### Post by Seantiago on 2006-09-26
Oh snap, doggs.  I just saw you need to make Sun your default java version if you wanna do that garbage I was trying.  Got it all figured out now.  Thanks to anyone who would have helped me out!

---

### Post by L2wis on 2006-09-27
> **Seantiago said:**
> Oh snap, doggs.  I just saw you need to make Sun your default java version if you wanna do that garbage I was trying.  Got it all figured out now.  Thanks to anyone who would have helped me out!

Hey dude i've got the same problem.... Where can i make sun my default java?

---

### Post by Ramses de Norre on 2006-09-27
```
sudo update-alternatives --config java
sudo update-alternatives --config javac
```

---

### Post by hod139 on 2006-09-30
You shouldn't use those commands, you should use 
```

 sudo update-java-alternatives -s java-1.5.0-sun
```
see this post for more info [http://ubuntuforums.org/showthread.php?t=201378](http://ubuntuforums.org/showthread.php?t=201378)

---

### Post by virtualXTC on 2012-06-07
none of this worked for me (Ubuntu 12.02, openjdk 6)

what did work was:

```
sudo cp /usr/lib/jvm/java-1.6.0-openjdk-amd64/bin/javac /usr/lib/jvm/java-1.6.0-openjdk-amd64/jre/bin/

```

---

### Post by L2wis on 2012-06-07
Thats the best thread revival i've ever been involved in! :)

Thanks for adding that information! And nice one finding this thread!! 

6 years ago.... wow! Time flies!

---

### Post by beriaanirudh on 2012-08-28
just for info  :: even i had same problem . m using mint 13 ( mint is ubuntu based ) . 
i did update-alternatives , BUT LOGGED IN AS ROOT. it worked for me :)

---

