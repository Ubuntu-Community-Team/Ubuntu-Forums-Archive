---
title: "Cannot run a Java Applet from Eclipse"
date: 2006-10-09
forum: Programming Talk
---

### Post by Nickb-k on 2006-10-09
Hello,

I am trying to run a very basic applet from Eclipse 3.1.2 on Ubuntu 6.02.

java -version
```
java version "1.5.0_06"
Java(TM) 2 Runtime Environment, Standard Edition (build 1.5.0_06-b05)
Java HotSpot(TM) Client VM (build 1.5.0_06-b05, mixed mode, sharing)
```

Eclipse is using java-1.5.0-sun. My Classpath is:


```
CLASSPATH=:/usr/lib/jvm/java-1.5.0-sun/bin:/usr/lib/jvm/java-1.5.0-sun/:/usr/lib/jvm/java-1.5.0-sun/lib

```

When I run the applet in Eclipse, I get this error:

```

Exception in thread "main" java.lang.NoClassDefFoundError: sun.applet.AppletViewer
   at gnu.java.lang.MainThread.run(libgcj.so.7)
Caused by: java.lang.ClassNotFoundException: sun.applet.AppletViewer not found in gnu.gcj.runtime.SystemClassLoader{urls=[file:/home/nick/Java/Test-Applet/Test1/], parent=gnu.gcj.runtime.ExtensionClassLoader{urls=[], parent=null}}
   at java.net.URLClassLoader.findClass(libgcj.so.7)
   at java.lang.ClassLoader.loadClass(libgcj.so.7)
   at java.lang.ClassLoader.loadClass(libgcj.so.7)
   at java.lang.Class.forName(libgcj.so.7)
   at gnu.java.lang.MainThread.run(libgcj.so.7)

```

I am interpreting this error as meaning that Eclipse cant find sun.applet.AppletViewer.  When I run AppletViewer from bash, I can use it fine, and so far as I can tell I have a working java insatllation - I can compile using javac and I can view applets.

Anyone have any tips? (Even a pointer toward some documentation for Gnu.gcj.runtime.SystemClassLoader would help)

Thanks in advance

Nick

---

### Post by Nickb-k on 2006-10-10
Ok - even a pointer to an Eclipse support forum would be really usefull.  Considering how widely used Eclipse is there seems to be a lack of community support for it. :(

---

### Post by Nickb-k on 2006-10-10
The problem is that Eclipse is using java-1.4.2-gcj-4.1-1.4.2.0 - a JRE not an SDK/JDK.  So now I need to figure out how to make eclipse use the JDK...

---

### Post by gmarton on 2006-10-10
Hi,
I have not used the eclipse from the Ubuntu repositories but downloaded from here :
[http://www.easyeclipse.org/site/distributions/index.html](http://www.easyeclipse.org/site/distributions/index.html)

The ones available already have the plugins you need installed( I use the PHP one) 

Try downloading/running one from the link above. If you need to switch java around use this commend:
> sudo update-alternatives --config java

---

### Post by Nickb-k on 2006-10-10
Ok, Problem solved.  As I didnt find anything here to help my woes, I'll post the solution.

The symptom was Eclipse erroring when tryin the launch an applet.  If you switch to Debug perspective, you can see in the window on the top leftm which JVM is being executed.  In my case, Eclipse was tyring to use the libgcj (GNU Java) JVM, causing Eclipse to throw the error described above, becuase there is to AppletViewer class in libgc7.

The solution - Click Run > Run then click on JRE and select the required JRE.

Simple! :)

---

### Post by kennycason on 2008-07-26
Hi, 
I have also had this problem for about a year now.. 
I tried all the solutions here and nothing worked for me. 
any other ideas?

>The solution - Click Run > Run then click on JRE and select the required JRE.
I tried this however only have one available JRE to choose from. 
java-1.5.0-gcj-4.2-1.5.0.0

Thanks

---

### Post by HotCupOfJava on 2008-07-26
Go and get you another JRE or JDK from the repositories - there are several available there. Run Synaptic and search for "java" and you will see lots of options.

---

### Post by MasterAchilles on 2009-04-07
I am also having this problem. I downloaded new JRE's but I don't know where to find them in order to add them to Java.

---

### Post by No_Mercy on 2009-05-28
After installing new JRE's: go to: Eclipse>Window>Preferences> Installed JREs. Then click "search" and open directory: /usr/lib/jvm. Start the search and all available JREs will be automaticaly added to Eclipse. After that u may choose what JRE u want ot use.

---

### Post by v.sakko on 2009-09-03
Thanks! Very helpful.

---

