---
title: "OutOfMemoryError: PermGen space when running eclipse 3.3 on ubuntu"
date: 2007-08-07
forum: Programming Talk
---

### Post by yinglcs2 on 2007-08-07
hi,

I keep getting this error when I run eclipse 3.3 on ubuntu.  Can anyone help?

$ Exception in thread "Tomcat Ping Thread" java.lang.OutOfMemoryError: PermGen space
        at sun.net.www.protocol.http.HttpURLConnection.<init>(HttpURLConnection.java:225)
        at sun.net.[www.protocol.http.Handler.openConnection(Handler.java:44](www.protocol.http.Handler.openConnection(Handler.java:44))
        at sun.net.[www.protocol.http.Handler.openConnection(Handler.java:39](www.protocol.http.Handler.openConnection(Handler.java:39))
        at java.net.URL.openConnection(URL.java:945)
        at org.eclipse.jst.server.tomcat.core.internal.PingThread.ping(PingThread.java:86)
        at org.eclipse.jst.server.tomcat.core.internal.PingThread$1.run(PingThread.java:53)
Exception in thread "org.eclipse.jdt.debug: JDI Event Dispatcher" java.lang.OutOfMemoryError: PermGen space
        at java.lang.ClassLoader.defineClass1(Native Method)
        at java.lang.ClassLoader.defineClass(ClassLoader.java:620)
        at org.eclipse.osgi.internal.baseadaptor.DefaultClassLoader.defineClass(DefaultClassLoader.java:161)
        at org.eclipse.osgi.baseadaptor.loader.ClasspathManager.defineClass(ClasspathManager.java:501)
        at org.eclipse.osgi.baseadaptor.loader.ClasspathManager.findClassImpl(ClasspathManager.java:471)
        at org.eclipse.osgi.baseadaptor.loader.ClasspathManager.findLocalClassImpl(ClasspathManager.java:430)
        at org.eclipse.osgi.baseadaptor.loader.ClasspathManager.findLocalClass(ClasspathManager.java:413)
        at org.eclipse.osgi.internal.baseadaptor.DefaultClassLoader.findLocalClass(DefaultClassLoader.java:189)
        at org.eclipse.osgi.framework.internal.core.BundleLoader.findLocalClass(BundleLoader.java:340)
        at org.eclipse.osgi.framework.internal.core.BundleLoader.findClassInternal(BundleLoader.java:408)
        at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(BundleLoader.java:369)
        at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(BundleLoader.java:357)
        at org.eclipse.osgi.internal.baseadaptor.DefaultClassLoader.loadClass(DefaultClassLoader.java:83)
        at java.lang.ClassLoader.loadClass(ClassLoader.java:251)
        at java.lang.ClassLoader.loadClassInternal(ClassLoader.java:319)
        at org.eclipse.jdi.internal.event.EventQueueImpl.remove(EventQueueImpl.java:65)
        at org.eclipse.jdt.internal.debug.core.EventDispatcher.run(EventDispatcher.java:226)
        at java.lang.Thread.run(Thread.java:619)
java.lang.OutOfMemoryError: PermGen space
Exception in thread "Server Termination Thread" java.lang.OutOfMemoryError: PermGen space
Error while logging event loop exception:
java.lang.OutOfMemoryError: PermGen space
Logging exception:
java.lang.OutOfMemoryError: PermGen space

---

### Post by nitro_n2o on 2007-08-07
probably you'll need to increase the Java heap space here is how
[http://hausheer.osola.com/docs/5](http://hausheer.osola.com/docs/5) if the problem persists then it's something wrong with your installation maybe

---

### Post by edwardTheGreat on 2007-08-08
> **nitro_n2o said:**
> probably you'll need to increase the Java heap space here is how
[http://hausheer.osola.com/docs/5](http://hausheer.osola.com/docs/5) if the problem persists then it's something wrong with your installation maybe

Thats Right, it looks like your PermSize is running out of room.

I haven't done this on my ubuntu setup as yet, but I think this might be how to fix it
Go to where you set up your JAVA_HOME for example:

```
gedit ~/.bashrc
```

add
```
export JAVA_OPTS=-Xms128m -Xmx128m -XX:MaxPermSize=128m
```

Increasing the MaxPermSize should fix this error.

See here for more info
[http://www.unixville.com/~moazam/stories/2004/05/17/maxpermsizeAndHowItRelatesToTheOverallHeap.html]("http://www.unixville.com/~moazam/stories/2004/05/17/maxpermsizeAndHowItRelatesToTheOverallHeap.html")

Let us know if that helped... ;-)

---

### Post by tenmillionmilesaway on 2007-08-10
If you navigate to the directory where eclipse is installed (where the eclipse executable is) you will find a file called eclipse.ini  You should put the -XX:MaxPermSize option in here (along with any other vm options that you want to use when for running eclipse).
I don't know exactly what the PermGen space is but it is not the same as the heap size which is governed by the options -Xms -Xmx options.  see this page for more information: [http://wiki.eclipse.org/FAQ_How_do_I_increase_the_permgen_size_available_to_Eclipse%3F](http://wiki.eclipse.org/FAQ_How_do_I_increase_the_permgen_size_available_to_Eclipse%3F)

I have also read that sometimes on linux the eclipse.ini file is not read correctly, with someone else suggesting that each option in the file needs to be on a new line.  I'm not sure how you could test to make sure the eclipse.ini is read, but it *should *be.

It is also be possible to pass these options in manually by launching eclipse from the command line and adding the -vmargs stuff on the command line too: eg ```
eclipse -vmargs -Xms256m -Xmx512m -XX:MaxPermSize=128m
```

The PermGen problem tends to occur (afaik) when you have lots of plugins installed, this is why many eclipse users have multiple versions of eclipse with the minimum number of plugins that they need for the particular project.

Hope this helps

---

