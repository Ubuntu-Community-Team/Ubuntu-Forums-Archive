---
title: "Running Anything In Java Gives Error In Eclipse"
date: 2009-05-31
forum: Programming Talk
---

### Post by sdlynx on 2009-05-31
Whenever I try to run anything (Application or Applet) it gives me this error:

```
Exception in thread "main" java.lang.NoClassDefFoundError: sun.applet.AppletViewer
    at gnu.java.lang.MainThread.run(libgcj.so.90) Caused by: java.lang.ClassNotFoundException: sun.applet.AppletViewer not found in gnu.gcj.runtime.SystemClassLoader{urls=[file:/home/*username*/workspace/applet/], parent=gnu.gcj.runtime.ExtensionClassLoader{urls=[], parent=null}}
    at java.net.URLClassLoader.findClass(libgcj.so.90)
    at gnu.gcj.runtime.SystemClassLoader.findClass(libgcj.so.90)
    at java.lang.ClassLoader.loadClass(libgcj.so.90)
    at java.lang.ClassLoader.loadClass(libgcj.so.90)
    at gnu.java.lang.MainThread.run(libgcj.so.90)
```
These errors are from the applet I tried to run.  The exact same error occurs when I try to run an application exept it does not say sun.applet.AppletViewer it says something else.

Does anybody know how to fix this?

---

### Post by Ruhe on 2009-05-31
Install Sun JDK. And change it to default:

[LIST]
[*]Open a Terminal window
[*]Run sudo apt-get install sun-java6-jdk to install Sun jdk.
[*]Run sudo update-java-alternatives -l to see the current configuration and possibilities.
[*]Run sudo update-java-alternatives -s XXXX to set the XXX java version as default. For Sun Java 6 this would be sudo update-java-alternatives -s java-6-sun
[*]Run java -version to ensure that the correct version is being called.
[/LIST]

From [ubuntu help pages]("https://help.ubuntu.com/community/Java").

---

### Post by sdlynx on 2009-05-31
I already tried that and I did it again but to no avail.  During the update-java-alternatives process it only updated about half the things if that can give you any lead.  It said no alternative for the other half.

---

### Post by Ruhe on 2009-06-01
So running **java -version** gives you gcj?

Try to uninstall gcj and check that sun jdk is installed.
Then again try to update default java version, and check what returns **java -version**.

And one more thing:
Go to eclipse preferences, Java -> Installed JREs.
If sun jdk isn't in the list, then add it and set as default.

---

### Post by sdlynx on 2009-06-01
Thanks so much! That worked.  I just uninstalled everything involving gcj, did sudo update-java-alternatives -s sun-6-java (or whatever it was) and it had me reselect a workspace when I opened Eclipse but it worked. =]

---

