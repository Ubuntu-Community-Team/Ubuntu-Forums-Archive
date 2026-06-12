---
title: "frostwire"
date: 2008-06-27
forum: New to Ubuntu
---

### Post by fignig on 2008-06-27
so i tried installing frostwire thru the repository and it doesn't seem to have installed the entire thing. just seeing what i need to do to make this work.

call me back, we'll figure this thing out TOGETHER!

---

### Post by Journeyman on 2008-06-27
what is missing or not working?

---

### Post by fignig on 2008-06-28
> **Journeyman said:**
> what is missing or not working?

the entire program. it's almost like it's not there, but it says it is.

---

### Post by Frak on 2008-06-28
```
sudo apt-get install sun-java6-jre
wget http://iacchus.frostwire.com/frostwire/4.13.5/frostwire-4.13.5.i586.deb
sudo dpkg -i frostwire-4.13.5.i586.deb
sudo update-alternatives --config java # select the one that says "/usr/lib/jvm/ia32-java-6-sun/jre/bin/java"

```

That should install the latest version for you.

---

### Post by mrsudo on 2008-06-28
i have the same problem.
i installed through synaptic and it shows in my menu except everytime i click o it, it doesnt respond.  even through command.

---

### Post by mrsudo on 2008-06-28
i have the same problem.
i installed through synaptic and it shows in my menu except everytime i click o it, it doesnt respond.  even through command.

---

### Post by tekguy on 2008-06-28
Try to run it from the command line and see what you get. I am having the same problem and I am getting:

```
Starting FrostWire...
Java exec found in PATH. Verifying...
Suitable java version found [java = 1.6.0]
Configuring environment...
Loading FrostWire:
java.lang.UnsatisfiedLinkError: Can't load library: /usr/lib/jvm/java-6-openjdk/jre/lib/i386/motif21/libmawt.so
	at java.lang.ClassLoader.loadLibrary(ClassLoader.java:1666)
	at java.lang.Runtime.load0(Runtime.java:787)
	at java.lang.System.load(System.java:1022)
	at java.lang.ClassLoader$NativeLibrary.load(Native Method)
	at java.lang.ClassLoader.loadLibrary0(ClassLoader.java:1767)
	at java.lang.ClassLoader.loadLibrary(ClassLoader.java:1684)
	at java.lang.Runtime.loadLibrary0(Runtime.java:840)
	at java.lang.System.loadLibrary(System.java:1047)
	at sun.security.action.LoadLibraryAction.run(LoadLibraryAction.java:67)
	at sun.security.action.LoadLibraryAction.run(LoadLibraryAction.java:47)
	at java.security.AccessController.doPrivileged(Native Method)
	at java.awt.Toolkit.loadLibraries(Toolkit.java:1610)
	at java.awt.Toolkit.<clinit>(Toolkit.java:1632)
	at com.limegroup.gnutella.gui.Main.showInitialSplash(Main.java:67)
	at com.limegroup.gnutella.gui.Main.main(Main.java:39)


******************************************************************
Something went wrong with FrostWire.
Maybe you're using the wrong version of Java?
(FrostWire is tested against and works best with with Sun's JRE, Java 1.4+)
The version of Java in your PATH is:
java version "1.6.0"
OpenJDK Runtime Environment (build 1.6.0-b09)
OpenJDK Client VM (build 1.6.0-b09, mixed mode, sharing)
```

---

### Post by Zopiac on 2008-06-28
> **Frak said:**
> ```
wget http://iacchus.frostwire.com/frostwire/4.13.5/frostwire-4.13.5.i586.deb
sudo dpkg -i frostwire-4.13.5.i586.deb
```

That should install the latest version for you.

i tried that; (menu)>internet>frostwire does nothing for me

---

### Post by rossjman1 on 2008-06-28
Try
sudo apt-get remove frostwire
then try installing the version on frostwire.com

---

### Post by Zopiac on 2008-06-28
> **rossjman1 said:**
> Try
sudo apt-get remove frostwire
then try installing the version on frostwire.com

still doesnt work for me...

---

### Post by swaknight on 2008-06-28
I am getting the same error and i am using Kubuntu. I tried installing it via terminal and frostwire.com

---

### Post by atomkarinca on 2008-06-28
If you haven't done already, install Java Runtime Environment. Open up a terminal (Applications > Accessories > Terminal) and type:

```
sudo apt-get install sun-java6-jre
```

then change your in-use java version to jre:

```
sudo update-alternatives --config java
```

and select the one saying sun-java6-jre. Now try to launch Frostwire again.

---

### Post by |{urse on 2008-06-28
I know this doesn't exactly fiXX0r ur problem but.. for all you hardcore audiophiles/videophiles that need your fix and cant get frostwire working,,

```

-inurl:(htm|html|php) intitle:"index of" +"last modified" +"parent directory" +description +size +(wma|mp3) "Kleptones"
```

Paste the above into a google search (not the address bar, the search box on google.com) change the "Kleptones" part to whatever you want "Whatever" and click search.. you can browse open ftp directories and unsecured servers to find literally w/e u want music-wise. I have yet to not be able to find a song.

you can do the same for video

```
-inurl:(htm|html|php) intitle:"index of" +"last modified" +"parent directory" +description +size +(mpg|avi) "fight club"
```

though it isn't as useful (not many people host/share video on the interwebs nowadays)

---

### Post by damis648 on 2008-06-28
Install java runtime as the poster two above me said! This is how to fix it.

---

### Post by Frak on 2008-06-28
Install JRE, the IcedTea replacement isn't up to par for what it needs.

---

### Post by |{urse on 2008-06-28
icedtea is a pain in the butttttt..

lol frak the link in ur sig.. I was watchin tht the other day. lmao poor kid, i bet the real nerds at school pick on him alot.

---

### Post by swaknight on 2008-06-28
i have the Java Jre runtime eviroment, 1.6  the newest i beleive  and i still get the same error. infact, in the error it tells me that i have runtime 1.6

```
Starting FrostWire...
Java exec found in PATH. Verifying...
Suitable java version found [java = 1.6.0]
Configuring environment...
Loading FrostWire:
java.lang.UnsatisfiedLinkError: Can't load library: /usr/lib/jvm/java-6-openjdk/jre/lib/i386/motif21/libmawt.so
        at java.lang.ClassLoader.loadLibrary(ClassLoader.java:1666)
        at java.lang.Runtime.load0(Runtime.java:787)
        at java.lang.System.load(System.java:1022)
        at java.lang.ClassLoader$NativeLibrary.load(Native Method)
        at java.lang.ClassLoader.loadLibrary0(ClassLoader.java:1767)
        at java.lang.ClassLoader.loadLibrary(ClassLoader.java:1684)
        at java.lang.Runtime.loadLibrary0(Runtime.java:840)
        at java.lang.System.loadLibrary(System.java:1047)
        at sun.security.action.LoadLibraryAction.run(LoadLibraryAction.java:67)
        at sun.security.action.LoadLibraryAction.run(LoadLibraryAction.java:47)
        at java.security.AccessController.doPrivileged(Native Method)
        at java.awt.Toolkit.loadLibraries(Toolkit.java:1610)
        at java.awt.Toolkit.<clinit>(Toolkit.java:1632)
        at com.limegroup.gnutella.gui.Main.showInitialSplash(Main.java:67)
        at com.limegroup.gnutella.gui.Main.main(Main.java:39)


******************************************************************
Something went wrong with FrostWire.
Maybe you're using the wrong version of Java?
(FrostWire is tested against and works best with with Sun's JRE, Java 1.4+)
The version of Java in your PATH is:
_java version "1.6.0"_
OpenJDK Runtime Environment (build 1.6.0-b09)
OpenJDK Server VM (build 1.6.0-b09, mixed mode)

```


see

---

### Post by Sukarn on 2008-06-28
If you're running 64-bit Ubuntu, then you need to install ia32-sun-java6-bin from the repository and then type
```

sudo update-alternatives --config java

```
and select the one that says "/usr/lib/jvm/ia32-java-6-sun/jre/bin/java"

---

### Post by fignig on 2008-06-28
> **Frak said:**
> ```
wget http://iacchus.frostwire.com/frostwire/4.13.5/frostwire-4.13.5.i586.deb
sudo dpkg -i frostwire-4.13.5.i586.deb
```

That should install the latest version for you.

i sudo apt-get remove frostwire, then i installed w/ this code. but i still seem to have problems opening up frostwire, it just won't open. not even run program or terminal or clicking the icon. wtf?

---

### Post by rage-against-windows on 2008-06-28
sun-java6-jre from the synaptic package manager, and then go to [http://www.frostwire.com/](http://www.frostwire.com/) and download the deb install frostwire 4.13.5 for ubuntu. Worked like a charm for me.

---

### Post by Zopiac on 2008-06-28
nvm, sukarn's post fixed my problem!

---

### Post by tekguy on 2008-06-29
> **swaknight said:**
> i have the Java Jre runtime eviroment, 1.6  the newest i beleive  and i still get the same error. infact, in the error it tells me that i have runtime 1.6

```
Starting FrostWire...
Java exec found in PATH. Verifying...
Suitable java version found [java = 1.6.0]
Configuring environment...
Loading FrostWire:
java.lang.UnsatisfiedLinkError: Can't load library: /usr/lib/jvm/java-6-openjdk/jre/lib/i386/motif21/libmawt.so
        at java.lang.ClassLoader.loadLibrary(ClassLoader.java:1666)
        at java.lang.Runtime.load0(Runtime.java:787)
        at java.lang.System.load(System.java:1022)
        at java.lang.ClassLoader$NativeLibrary.load(Native Method)
        at java.lang.ClassLoader.loadLibrary0(ClassLoader.java:1767)
        at java.lang.ClassLoader.loadLibrary(ClassLoader.java:1684)
        at java.lang.Runtime.loadLibrary0(Runtime.java:840)
        at java.lang.System.loadLibrary(System.java:1047)
        at sun.security.action.LoadLibraryAction.run(LoadLibraryAction.java:67)
        at sun.security.action.LoadLibraryAction.run(LoadLibraryAction.java:47)
        at java.security.AccessController.doPrivileged(Native Method)
        at java.awt.Toolkit.loadLibraries(Toolkit.java:1610)
        at java.awt.Toolkit.<clinit>(Toolkit.java:1632)
        at com.limegroup.gnutella.gui.Main.showInitialSplash(Main.java:67)
        at com.limegroup.gnutella.gui.Main.main(Main.java:39)


******************************************************************
Something went wrong with FrostWire.
Maybe you're using the wrong version of Java?
(FrostWire is tested against and works best with with Sun's JRE, Java 1.4+)
The version of Java in your PATH is:
_java version "1.6.0"_
OpenJDK Runtime Environment (build 1.6.0-b09)
OpenJDK Server VM (build 1.6.0-b09, mixed mode)

```


see

I had the same thing. I ran the following and selected the one that said java-6-sun. The one that was selected was java-6-open:

```
sudo update-alternatives --config java
```

---

### Post by lwvmobile on 2008-06-29
Don't forget to install Sun Java JRE 1.5 or above. After quickly checking the Synaptic Package Manager, that is sun-java5-jre so either install it from there or
```
sudo apt-get install sun-java5-jre
```

Hope that helps somebody.

---

