---
title: "Arduino &amp; Ubuntu 11.10 Not working"
date: 2011-12-21
forum: New to Ubuntu
---

### Post by NotWindows on 2011-12-21
Hello All!

I have enabled some packages in Synaptic Package Manager and can't get Arduino Uno IDE to run. After that I installed the packages for Arduino and still can't get the IDE to come up on the screen(won't run).

What do I need to do to get Arduino Uno IDE to work with Ubuntu 11.10? I sure don't want to use windows if I don't have to!

Thanks,
Kevin

---

### Post by Paqman on 2011-12-22
It should just work (it does for me). A good way to check for problems running applications on Ubuntu is to run it in a terminal and then read the output.

Hit Ctrl-Alt-T to open a terminal and launch arduino by typing:
```
arduino
```
Then copy and paste the output into some [noparse]```

```[/noparse] tags here.

---

### Post by NotWindows on 2011-12-22
Paqman,

When I bring up Terminal and type in arduino it comes up fine! What's going on?

Thanks,
Kevin

---

### Post by Paqman on 2011-12-23
Don't know. How exactly are you trying to launch it that doesn't work?

---

### Post by NotWindows on 2011-12-23
I am trying the file named arduino in the folder Arduino-1.0 it is supposed to be a text or script file I think! If that is wrong which one do I need to use?

Thanks,
Kevin

---

### Post by Tux Aubrey on 2011-12-25
The program file for Arduino lives in /usr/bin

---

### Post by NotWindows on 2011-12-27
Got it and it works great!

Thanks,
Kevin

---

### Post by polycopter on 2012-02-05
After I choose a folder for sketches (on launching arduino IDE), I get this:

java.lang.UnsatisfiedLinkError: no rxtxSerial in java.library.path thrown while loading gnu.io.RXTXCommDriver
Exception in thread "main" java.lang.UnsatisfiedLinkError: no rxtxSerial in java.library.path
    at java.lang.ClassLoader.loadLibrary(ClassLoader.java:1738)
    at java.lang.Runtime.loadLibrary0(Runtime.java:823)
    at java.lang.System.loadLibrary(System.java:1028)
    at gnu.io.CommPortIdentifier.<clinit>(CommPortIdentifier.java:123)
    at processing.app.Editor.populateSerialMenu(Editor.java:965)
    at processing.app.Editor.buildToolsMenu(Editor.java:717)
    at processing.app.Editor.buildMenuBar(Editor.java:502)
    at processing.app.Editor.<init>(Editor.java:194)
    at processing.app.Base.handleOpen(Base.java:709)
    at processing.app.Base.handleOpen(Base.java:674)
    at processing.app.Base.handleNew(Base.java:571)
    at processing.app.Base.<init>(Base.java:311)
    at processing.app.Base.main(Base.java:200)

can you help?

---

