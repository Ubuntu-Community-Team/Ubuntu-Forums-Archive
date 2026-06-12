---
title: "java version different from javac"
date: 2008-04-22
forum: New to Ubuntu
---

### Post by koba101 on 2008-04-22
Hi,

When I type the version of javac in the terminal i get the following:


[PHP]javac 1.6.0_03[/PHP]


However the java version is :
[PHP]
java version "1.5.0"
gij (GNU libgcj) version 4.2.1 (Ubuntu 4.2.1-5ubuntu5)

Copyright (C) 2007 Free Software Foundation, Inc.
This is free software; see the source for copying conditions.  There is NO
warranty; not even for MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.
[/PHP]

So the complier is 1.6 yet the runtime it java5, how do i fix this?

---

### Post by Hallvor on 2008-04-22
Try this:

```
sudo update-java-alternatives
```

Hopefully you get to a screen where you can select the java version you want. Haven`t tested it myself...

---

### Post by crs0328 on 2008-04-22
You might make sure you have java installed correctly through the Synaptic Package Manager.
sun-java5-jdk  or  sun-java6-jdk

Once you are sure you have the version of java you want to use installed, you need to match the java compiler to the correct version of java.

This will give you the choice to choose which version of java on your computer you want to use:
```
sudo update-alternatives --config java
```

This will give you a choice to choose which compiler you want to use. (i.e. version 1.5.0 or 1.6.0)
```
sudo update-alternatives --config javac 
```

Once they are using the same java version, you should be set to go.

---

### Post by koba101 on 2008-04-22
alright this worked out fine...just one thing...how do i uninstall java 5 since i already have java 6?

I'm actually having similar problems similar to this like having two versions of alsa...how can i remove those programs?

---

### Post by crs0328 on 2008-04-25
To uninstall java5, just use the Synaptic Package Manager.  Search for sun-java5-jdk and it will remove itself and all the dependencies (of course after you hit apply).  I'm not familiar with alsa, but I would assume you could uninstall it the same way.

---

### Post by SOULRiDER on 2008-04-25
> **koba101 said:**
> alright this worked out fine...just one thing...how do i uninstall java 5 since i already have java 6?

I'm actually having similar problems similar to this like having two versions of alsa...how can i remove those programs?

If you have the Sun JRE,
```
sudo aptitude remove sun-java5-jre
```
That however is not Java, its GNU's implementation of Java, im not sure what the package is called. Look for packages that begin with GCJ.

---

