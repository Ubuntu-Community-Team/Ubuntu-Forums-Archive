---
title: "netbeans blank window"
date: 2008-05-06
forum: Programming Talk
---

### Post by sanjaymk on 2008-05-06
hello all,

i'm trying to install the latest version of netbeans from [http://download.netbeans.org/netbeans/6.1/final/](http://download.netbeans.org/netbeans/6.1/final/), after I downloaded and ran the .sh file, I get a blank netbeans window(with no widgets in it).  

The contents of the terminal are ..

[I]Configuring the installer...
Searching for JVM on the system...
Preparing bundled JVM ...
Extracting installation data...
Running the installer wizard...
/usr/share/themes/Human/gtk-2.0/gtkrc:71: Engine "ubuntulooks" is unsupported, ignoring
/usr/share/themes/Human/gtk-2.0/gtkrc:242: Priority specification is unsupported, ignoring
[/I]


I'm using the UBUNTU ver.7.10 and when I do a java -version I get 

java version "1.5.0_13"
Java(TM) 2 Runtime Environment, Standard Edition (build 1.5.0_13-b05)
Java HotSpot(TM) Server VM (build 1.5.0_13-b05, mixed mode)


This was the same behavior when I tried to install netbeans from the synaptic manager last month OR when I tried to get the JDK+netbeans pack version 6.0

Any help would be appreciated.

Thanks,
Sanjay.

---

### Post by apoth on 2008-05-07
Try disabling compiz or running the following in a terminal and then launching netbeans from the same terminal:

```
export AWT_TOOLKIT=MToolkit
```

---

