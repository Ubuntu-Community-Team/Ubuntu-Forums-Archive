---
title: "FrostWire not Working"
date: 2008-05-02
forum: New to Ubuntu
---

### Post by System Monitor on 2008-05-02
When I try to open frostwire it does not do anything?

I tried frostwire at the command line but I am not sure what the response means. Any help with what I should do to fix it?

```
sam@sam-desktop:~$ frostwire
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

### Post by perlluver on 2008-05-02
> **System Monitor said:**
> When I try to open frostwire it does not do anything?

I tried frostwire at the command line but I am not sure what the response means. Any help with what I should do to fix it?

```
sam@sam-desktop:~$ frostwire
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

Go to add remove programs, make sure all available applications is marked, and download Sun Java.  Then run sudo update java-alternatives, I believe.  And pick Sun Java instead of OpenJDK.

---

### Post by System Monitor on 2008-05-02
got command not found for "dpkg-configure java-config"

---

### Post by perlluver on 2008-05-02
> **System Monitor said:**
> got command not found for "dpkg-configure java-config"

sudo update java-alternatives sorry about that.

---

### Post by System Monitor on 2008-05-02
Got "sudo: update: command not found"

---

### Post by perlluver on 2008-05-02
> **System Monitor said:**
> Got "sudo: update: command not found"

sudo update-alternatives --config java that is from official docs, it should work.

---

