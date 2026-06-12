---
title: "Robocode java.awt.headlessexception error"
date: 2012-06-01
forum: Programming Talk
---

### Post by gameguy on 2012-06-01
I just installed 12.04, and tried to install robocode using it. It chucked a headlessexception, so I tried using the one off sourceforge, which also chucked a headlessexception (this time during the installation process). I was using the latest version in both cases.

The error:
```

No robocode.properties, using defaults.
java.awt.HeadlessException
    at java.awt.GraphicsEnvironment.checkHeadless(GraphicsEnvironment.java:173)
    at java.awt.Window.<init>(Window.java:476)
    at java.awt.Frame.<init>(Frame.java:419)
    at java.awt.Frame.<init>(Frame.java:384)
    at javax.swing.SwingUtilities$SharedOwnerFrame.<init>(SwingUtilities.java:1754)
    at javax.swing.SwingUtilities.getSharedOwnerFrame(SwingUtilities.java:1831)
    at javax.swing.JWindow.<init>(JWindow.java:185)
    at javax.swing.JWindow.<init>(JWindow.java:137)
    at robocode.dialog.RcSplashScreen.<init>(Unknown Source)
    at robocode.manager.WindowManager.showSplashScreen(Unknown Source)
    at robocode.Robocode.run(Unknown Source)
    at robocode.Robocode.access$3(Unknown Source)
    at robocode.Robocode$1.run(Unknown Source)

```

I am using the latest gcj and javac, and haven't been able to work out how to install the jre off oracle's website (I've downloaded jre for linux 64-bit, but it says they're just the binaries, and I don't know how to run robocode using it)

---

### Post by sammiev on 2012-06-01
[This]("http://sites.google.com/site/easylinuxtipsproject/java") should help you out. :)

---

### Post by gameguy on 2012-06-02
Done that, get the exact same error...

---

### Post by sammiev on 2012-06-02
> **gameguy said:**
> Done that, get the exact same error...

Need to restart your browser after you add java.

---

### Post by gameguy on 2012-06-02
It's not running in browser...
And gcj, java, and javac still work fine when compiling / running normal java programs.

---

### Post by Zugzwang on 2012-06-02
Hi Gameguy,

it depends on what is a "normal" Java program for you. If headless exceptions are thrown, then you probably can't run programs with GUI, so forget about the gcj for such use cases. You want a proper Java runtime environment. I would suggest that you install the JRE of openjdk. This can be done using the package manager. Just install the "openjdk-7-jre" package. It replaces the SUN JRE on all newer Ubuntu distributions for almost all purposes. Finally, since you then will have multiple compilers and "java" commands on your computer, run "update-alternatives --config java" to select the openJDK.

---

### Post by gameguy on 2012-06-02
So what I ran was:
```

sudo apt-get install openjdk-7-jre
sudo update-alternatives --config java

```First command worked fine, second came up with this:

```

  Selection    Path                                            Priority   Status
------------------------------------------------------------
  0            /usr/lib/jvm/java-6-openjdk-amd64/jre/bin/java   1061      auto mode
  1            /opt/java/64/jre1.7.0_04/bin/java                1         manual mode
  2            /usr/bin/gij-4.6                                 1046      manual mode
  3            /usr/lib/jvm/java-6-openjdk-amd64/jre/bin/java   1061      manual mode
* 4            /usr/lib/jvm/java-7-openjdk-amd64/jre/bin/java   1051      manual mode

```I selected 4 at first, and it chucked the same error. I then tried the others - all came up with the headless error.

---

