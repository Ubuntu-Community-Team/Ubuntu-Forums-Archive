---
title: "Java-Gnome Help..."
date: 2010-06-18
forum: Programming Talk
---

### Post by KdotJ on 2010-06-18
Hey I hope someone can help or has some experience with the gtk bindings for Java.

I installed the java-gnome bindings from the Ubuntu repo's by following the instructions on [THIS]("http://java-gnome.sourceforge.net/4.0/get/ubuntu.php") webpage.

I also rebooted after doing so as I had other updates installed.

Then to test it out I copied the java code from [THIS]("http://java-gnome.sourceforge.net/4.0/doc/examples/button/ExamplePressMe.html") page.. which uses the bindings. I saved and compiled the file but it returned with 19 errors!
It's to do with the new packages I *apparently* installed. Below is one of the error messages from the trace.

```

ExamplePressMe.java:13: package org.gnome.gdk does not exist
import org.gnome.gdk.Event;
                    ^

```


Anyone have any ideas? Do I need to edit PATHs?

---

### Post by lykeion on 2010-06-19
It works fine, you just have to include gtk-4.0.jar in your classpath.

In ubuntu it's located in /usr/share/java/ after you've installed libjava-gnome-java

Check the readme [http://java-gnome.sourceforge.net/4.0/README.html](http://java-gnome.sourceforge.net/4.0/README.html) and look under the "Using the bindings" header

Good luck

---

