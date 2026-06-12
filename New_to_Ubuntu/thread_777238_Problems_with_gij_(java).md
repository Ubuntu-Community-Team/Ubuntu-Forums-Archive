---
title: "Problems with gij (java)"
date: 2008-05-01
forum: New to Ubuntu
---

### Post by NormR2 on 2008-05-01
I am not able to get gij to execute a jar file. I get an error for every jar file I use it with. The jar files were created on a Windows system and copied to the linux system. 
It seems that a file is missing:
libgtkpeer: libgtkpeer.so: cannot open shared object file: No such file or directory

Here are the terminal consoles for 3 attempts:

norm@norm-desktop:/media/sda5/JavaDevelopment/runtime$ gij -jar SearchFiles.jar
Exception in thread "main" java.awt.AWTError: Cannot load AWT toolkit: gnu.java.awt.peer.gtk.GtkToolkit
   at java.awt.Toolkit.getDefaultToolkit(libgcj.so.81)
   at java.awt.GraphicsEnvironment.getLocalGraphicsEnvironment(libgcj.so.81)
   at java.awt.Window.<init>(libgcj.so.81)
   at java.awt.Frame.<init>(libgcj.so.81)
   at NormsDev.SearchFiles.SearchFiles.<init>(SearchFiles.java:176)
   at NormsDev.SearchFiles.SearchFiles.main(SearchFiles.java:1183)
Caused by: java.lang.UnsatisfiedLinkError: libgtkpeer: libgtkpeer.so: cannot open shared object file: No such file or directory
   at java.lang.Runtime._load(libgcj.so.81)
   at java.lang.Runtime.loadLibrary(libgcj.so.81)
   at java.lang.System.loadLibrary(libgcj.so.81)
   at gnu.java.awt.peer.gtk.GtkToolkit.<clinit>(libgcj.so.81)
   at java.lang.Class.initializeClass(libgcj.so.81)
   at java.lang.Class.forName(libgcj.so.81)
   at java.awt.Toolkit.getDefaultToolkit(libgcj.so.81)
   ...5 more
norm@norm-desktop:/media/sda5/JavaDevelopment/runtime$ 


norm@norm-desktop:/media/sda5/JavaDevelopment/runtime$ gij -jar GuiBuilder.jar
Exception in thread "main" java.awt.AWTError: Cannot load AWT toolkit: gnu.java.awt.peer.gtk.GtkToolkit
   at java.awt.Toolkit.getDefaultToolkit(libgcj.so.81)
   at java.awt.GraphicsEnvironment.getLocalGraphicsEnvironment(libgcj.so.81)
   at java.awt.Window.<init>(libgcj.so.81)
   at java.awt.Frame.<init>(libgcj.so.81)
   at GuiBuilder.<init>(GuiBuilder.java:191)
   at GuiBuilder.main(GuiBuilder.java:935)
Caused by: java.lang.UnsatisfiedLinkError: libgtkpeer: libgtkpeer.so: cannot open shared object file: No such file or directory
   at java.lang.Runtime._load(libgcj.so.81)
   at java.lang.Runtime.loadLibrary(libgcj.so.81)
   at java.lang.System.loadLibrary(libgcj.so.81)
   at gnu.java.awt.peer.gtk.GtkToolkit.<clinit>(libgcj.so.81)
   at java.lang.Class.initializeClass(libgcj.so.81)
   at java.lang.Class.forName(libgcj.so.81)
   at java.awt.Toolkit.getDefaultToolkit(libgcj.so.81)
   ...5 more
norm@norm-desktop:/media/sda5/JavaDevelopment/runtime$ 

norm@norm-desktop:/media/sda5/JavaDevelopment/runtime$ gij -version
java version "1.5.0"
gij (GNU libgcj) version 4.2.1 (Ubuntu 4.2.1-5ubuntu5)

Copyright (C) 2007 Free Software Foundation, Inc.
This is free software; see the source for copying conditions.  There is NO
warranty; not even for MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.


norm@norm-desktop:/media/sda5/JavaDevelopment/runtime$ gij -jar URLSpider.jar
Exception in thread "main" java.awt.AWTError: Cannot load AWT toolkit: gnu.java.awt.peer.gtk.GtkToolkit
   at java.awt.Toolkit.getDefaultToolkit(libgcj.so.81)
   at java.awt.GraphicsEnvironment.getLocalGraphicsEnvironment(libgcj.so.81)
   at java.awt.Window.<init>(libgcj.so.81)
   at java.awt.Frame.<init>(libgcj.so.81)
   at URLSpider.<init>(URLSpider.java)
   at URLSpider.main(URLSpider.java)
Caused by: java.lang.UnsatisfiedLinkError: libgtkpeer: libgtkpeer.so: cannot open shared object file: No such file or directory
   at java.lang.Runtime._load(libgcj.so.81)
   at java.lang.Runtime.loadLibrary(libgcj.so.81)
   at java.lang.System.loadLibrary(libgcj.so.81)
   at gnu.java.awt.peer.gtk.GtkToolkit.<clinit>(libgcj.so.81)
   at java.lang.Class.initializeClass(libgcj.so.81)
   at java.lang.Class.forName(libgcj.so.81)
   at java.awt.Toolkit.getDefaultToolkit(libgcj.so.81)
   ...5 more


Thanks,
Norm

---

### Post by aldeby on 2008-05-19
You probably have both sun-java and gcj installed.

Try removing sun-java and all its dependencies (locate sun-java with synaptics search tool) and replace it with openjdk-jre

to open a java jar use 
```

java -jar filepath/filename.jar

```

I solved a similar problem this way. Hope it helps to you too!

---

### Post by NormR2 on 2008-05-19
Thanks for the reply. That's an old one.
I solved it by getting rid of gij. I installed Sun's java and replaced the link to gij with a link to Sun's java and it now works fine.

---

### Post by JDPG on 2009-06-19
[SIZE=3][FONT=Verdana]I'm using Ubuntu 7.04 "Feisty Fawn".

After downloading jre-6u14-linux-i586.bin from java.sun.com and executing it through terminal, the .bin file created files in-and folder named "jre1.6.0_14" in the same dir. (Home) where the .bin is saved...

I tried to use the java executable in the folder-.../[/FONT][/SIZE][SIZE=3][FONT=Verdana]jre1.6.0_14/bin[/FONT][/SIZE][SIZE=3][FONT=Verdana]/ as the command instead of the old gij command:

[FONT=Courier New]~$ sudo /home/jd/jre1.6.0_14/bin/java -jar /home/jd/NetBeansProjects/JavaApplication1/dist/JavaApplication1.jar[/FONT]

And it worked just fine.[/FONT][/SIZE]

---

