---
title: "Java problems on mint."
date: 2010-01-25
forum: Programming Talk
---

### Post by Garratt on 2010-01-25
Mint 7, based off Ubuntu 8.10. anyway this is the only linux programming forum I know of so I came here.
TBH  I'm not quite sure what I've done wrong. When I first installed I removed the ubuntu java libraries in synaptic and installed the sun-jdk-6 and then installed eclipse. I'm not sure if eclipse installs and uses GNU compiler by default or whether I can remove this from the system and only have the latest sun-JDK.

The executables in /usr/bin (java,javac,javadoc,javah,javap etc) all point to /etc/alternatives/*

the files in /etc/alt* point to /usr/lib/jvm/java-gcj/bin/*

libraries in /usr/lib/jvm include java-1.5.0-gjc-4.3.1.5.0.0 ; java-6-sun-1.6.0.16 ; a symlink folder java-6-sun that points to (java-6-sun-1.6.0.16); a symlink folder java-gcj that points to (java-1.5.0-gcj-4.3-1.5.0.0)

So I'm wondering should I change the symlinks to point to the sun executables ? because I have tried to use synaptic but every time I clicked on a lib to uninstal it would also want to try to uninstal eclipse as well. I want to keep eclipse, but I also want to be able to compile my .java files into .class files without receiving a million and 1 errors from command line. eg. I created a project in eclipse that worked fine, however had a LOT of output (this was by design) so I copied files from eclipse folder to a home dir to compile so I could keep all output in terminal, However I received so many errors, when there were no errors in eclipse. Errors like cannot import Scanner etc. random stuff.

This is what the system points to...

```

gcampton@gc-laptop ~ $ javac -v
Eclipse Java Compiler 0.894_R34x, 3.4.2 release, Copyright IBM Corp 2000, 2008. All rights reserved.
gcampton@gc-laptop ~ $ java
Usage: gij [OPTION] ... CLASS [ARGS] ...
          to invoke CLASS.main, or
       gij -jar [OPTION] ... JARFILE [ARGS] ...
          to execute a jar file
Try `gij --help' for more information.
gcampton@gc-laptop ~ $ java --version
java version "1.5.0"
gij (GNU libgcj) version 4.3.3

Copyright (C) 2007 Free Software Foundation, Inc.
This is free software; see the source for copying conditions.  There is NO
warranty; not even for MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.
gcampton@gc-laptop ~ $ gij
The program 'gij' is currently not installed.  You can install it by typing:
sudo apt-get install gij
bash: gij: command not found

```

Any help will be much appreciated. Thanks G.

---

### Post by Garratt on 2010-01-25
Eclipse version I'm guessing can be changed to something else it is:
Eclipse SDK
Version: 3.2.2
Build id: M20070212-1330 (Ubuntu version: 3.2.2-5ubuntu3)

So could I just uninstal this and gcj and install the normal eclipse?

In synaptic marking gjc-4.3-base for removal will remove the following:
```

ant-gcj
ant-optional-gcj
ecj
ecj-gcj
eclipse-gcj
eclipse-jdt-gcj
eclipse-pde-gcj
eclipse-platform-gcj
eclipse-rcp-gcj
gappletviewer-4.3
gcj-4.3
gij-4.3
gjdoc
java-gcj-compat
java-gcj-compat-dev
java-gcj-compat-headless
libantlr-java-gcj
libecj-java-gcj
libgcj-bc
libgcj9-0
libgcj9-0-awt
libgcj9-dev
libgcj9-jar
libgcj9-src
libjaxp1.3-java-gcj
liblog4j1.2-java-gcj
libswt3.2-gtk-gcj
libxerces2-java-gcj

```

---

### Post by arubislander on 2010-01-25
I would go ahead and uninstall the GNU java compiler. It will probably uninstall Eclipse as well: let it. Then be sure you've installed the sun java JDK. If you have, install Eclipse again and pay attention to what other packages it says it'll install along with it. It should realize there's already a JDK and work with that one.

---

### Post by Garratt on 2010-01-25
Ok, thanks. Will do and post back if I have any other problems. I guess I kinda came to that conclusion myself as well but that was after I realised Eclipse was actually the ubuntu version and not the normal version. :P
But yea it should be ok.

---

### Post by Seq on 2010-01-25
You can use `update-alternatives` to switch between alternative versions of java on the command line. It will handle updating the symlinks for you.

---

### Post by Garratt on 2010-01-25
oh well too late :s

```
gcampton@gc-laptop ~ $ java -version
java version "1.6.0_16"
Java(TM) SE Runtime Environment (build 1.6.0_16-b01)
Java HotSpot(TM) Server VM (build 14.2-b01, mixed mode)
gcampton@gc-laptop ~ $ javac -version
javac 1.6.0_16
gcampton@gc-laptop ~ $ 

```

---

### Post by Garratt on 2010-01-25
Much better anyway, installed the latest dev build 3.6 M4 and added to my ~/bin folder and made a custom launcher, problem solved.. so to speak, on the assumption I will break this OS and reformat, before the Ubuntu Eclipse team even get close to adding 3.6 to repos :D 

I'm stuck with this anyway due to the broadcom wireless driver issue that plagued the latest release of Ubuntu and Mint.

---

