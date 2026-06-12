---
title: "Java3d"
date: 2008-01-23
forum: Programming Talk
---

### Post by nhandler on 2008-01-23
I'm attempting to get Java 3d up and running on Ubuntu gutsy. I downloaded java3d-1_5_1-linux-i586.zip from sun's website. I then attempted to follow this page ([https://help.ubuntu.com/community/Java3dUbuntu](https://help.ubuntu.com/community/Java3dUbuntu)) to install it. Using the script from ([http://www.java3d.org/starting.html](http://www.java3d.org/starting.html)), I tried testing the Java 3d installation. I am able to generate a .class file using the javac command. When I try to execute the .class file by entering 'java Hello3d' in a terminal, I get this error:

> Java 3D ERROR : GLX extension is not supported
    GLX version 1.3 or higher is required
Exception in thread "main" java.lang.NullPointerException: Canvas3D: null GraphicsConfiguration
        at javax.media.j3d.Canvas3D.checkForValidGraphicsConfig(Canvas3D.java:963)
        at javax.media.j3d.Canvas3D.<init>(Canvas3D.java:1006)
        at com.sun.j3d.utils.universe.Viewer.<init>(Viewer.java:356)
        at com.sun.j3d.utils.universe.Viewer.<init>(Viewer.java:302)
        at com.sun.j3d.utils.universe.SimpleUniverse.<init>(SimpleUniverse.java:247)
        at com.sun.j3d.utils.universe.SimpleUniverse.<init>(SimpleUniverse.java:209)
        at com.sun.j3d.utils.universe.SimpleUniverse.<init>(SimpleUniverse.java:94)
        at Hello3d.<init>(Hello3d.java:13)
        at Hello3d.main(Hello3d.java:27)


Could someone help me get this working?

---

### Post by nhandler on 2008-01-24
bump

---

### Post by Zugzwang on 2008-01-25
What does "glxgears -info" reveal?

EDIT: Oh, and try "glxinfo" as well.

---

### Post by nhandler on 2008-01-25
> **Zugzwang said:**
> What does "glxgears -info" reveal?

EDIT: Oh, and try "glxinfo" as well.

glxgears -info gives:

> Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't get an RGB, Double-buffered visual


glxinfo gives:

> name of display: :0.0
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't find RGB GLX visual

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
0x21 16 tc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
0x39 32 tc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None


---

### Post by Zugzwang on 2008-01-26
Well, that appears to be the problem. So Java said: 
```

Java 3D ERROR : GLX extension is not supported
GLX version 1.3 or higher is require

```
You can use Wikipedia to look up what "GLX" is. The results of "glxinfo" contain the information that you XServer doesn't have that extension running at the moment, which is required for Java3D. So this is the wrong board as you have to get your support for 3D acceleration running ( I remember that you have to list the glx extension in the xorg.conf file, but I'm not sure about that. Try the "Multimedia & Video" board or google for a tutorial).

---

