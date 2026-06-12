---
title: "Eclipse + CVS = NoClassDefFoundError. Why?"
date: 2006-11-01
forum: Programming Talk
---

### Post by SlugO on 2006-11-01
I'm doing a Java programming project with a couple of friends for school and since I got sick of exchanging zips on ftp every time someone's done something I decided to use CVS with Eclipse.

Everything worked fine first. I set it up and synced the projects from Eclipse to CVS. However when I test if I can import them from there (exported in Windows, imported in Ubuntu) everything seems to be the same but I get the error```
Exception in thread "main" java.lang.NoClassDefFoundError: simulation/Simulation
```Why is that?! There was nothing like that before the CVS. Is it messing with the program code or what..? The same happened to my friend who downloaded the projects from the CVS.

I also noticed a few new errors that I don't think were there before:```
A cycle was detected in the build path of project: robotwarFW
The project cannot be built until build path errors are resolved
```(On second look they probably were there before)

Any idea what's wrong? I thought CVS wasn't supposed to change/add anything on its own ](*,)

Good thing there are many backups of the projects :)

---

### Post by amo-ej1 on 2006-11-02
Well the typical issue here, you've got gcj installed, some eclipse plugins don't like to work with gcj (or gcj doesn't like some plugins). I've had the same with some cdt related plugin.

Anyhow, what you should do:

a) launc ecipse from a console
b) you will see it probe for jdk's and probably it will find gcj and use it.

You might have update-alternatives set to point to the right (sun) jdk/jre. However eclipse is stubborn and doesn't care, therefore it probes it's own jdk's. 

So you should either start eclipse with the "-vm /path/to/your/sun/bin/java" flag, or uninstall the gcj (and ensure you have a sun jdk installed).

Edit: altough after reading your post again (don't seem to be that awake), perhaps you simply want to check what is really in cvs ? Do a checkout from the commandline and build it from the command line. Check the context of the files and the structure (some cvs web interface is probably installed which really suits checking out what is really into cvs). Perhaps somebody checked something in that wasn't supposed to be there ?

hope this helps

---

### Post by SlugO on 2006-11-02
Thanks for the suggestions. However this error also happens when I try to import the project from CVS to Eclipse that's running in Windows. And I don't think its using GCJ since I'm running the latest JDK 5 there. Also happened to my friend who's using Windows. The CVS server is on Ubuntu though but I don't think it affects anything.

I also doubt that the contents of the CVS could have changed since I'm the only person who's sent anything there. A friend just imported the projects once from there. When I browse CVS's content with Eclipse it shows the 4 projects that I sent there and CVSROOT which I created in the installation. So the contents should be fine too...

---

### Post by the_ice.e on 2009-04-07
I get this error when trying to run in eclipse
I have java.. at least i thing
```
Exception in thread "main" java.lang.NoClassDefFoundError: sun.applet.AppletViewer
   at gnu.java.lang.MainThread.run(libgcj.so.90)
Caused by: java.lang.ClassNotFoundException: sun.applet.AppletViewer not found in gnu.gcj.runtime.SystemClassLoader{urls=[file:/home/sebastian/workspace/Datum/], parent=gnu.gcj.runtime.ExtensionClassLoader{urls=[], parent=null}}
   at java.net.URLClassLoader.findClass(libgcj.so.90)
   at gnu.gcj.runtime.SystemClassLoader.findClass(libgcj.so.90)
   at java.lang.ClassLoader.loadClass(libgcj.so.90)
   at java.lang.ClassLoader.loadClass(libgcj.so.90)
   at gnu.java.lang.MainThread.run(libgcj.so.90)

```

any ideas whats wrong?

ou yea.. im new to eclipse & ubuntu

---

### Post by Zugzwang on 2009-04-07
> **the_ice.e said:**
> any ideas whats wrong?

ou yea.. im new to eclipse & ubuntu

Yes, see the stickies on how to configure Ubuntu to use the Sun JDK/JRE instead of the gnu one.

---

