---
title: "java.lang.UnsatisfiedLinkError: no gluegen-rt in java.library.path"
date: 2011-08-13
forum: Programming Talk
---

### Post by Kentucky88 on 2011-08-13
I am trying to run an open-source Java app called Jzy3d.  It uses Java Open GL bindings:

[http://jogamp.org/jogl/www/](http://jogamp.org/jogl/www/)

However, I am running 64-bit OpenJDK and I am linking with jogl.jar and gluegen-rt.jar files found in /usr/share/java.  I think they were installed when I added jogl and gluegen-rt through Synaptic Package Manager, or maybe they were just there to begin with.  Anyhow, when I run my application, I get the error message below.  The JOGL bindings simply bind Java code to the native Open GL libraries.  I think the message below is telling me that I am missing gluegen-rt.so library files.  Indeed, there is no gluegen-rt.so (only gluegen-rt.jar) in my /usr/share/java.  Am I interpretting the error correctly?  If so, where would I find gluegen-rt.so / jogl.so files?

[PHP]
Exception in thread "AWT-EventQueue-0" java.lang.UnsatisfiedLinkError: no gluegen-rt in java.library.path
    at java.lang.ClassLoader.loadLibrary(ClassLoader.java:1681)
    at java.lang.Runtime.loadLibrary0(Runtime.java:840)
    at java.lang.System.loadLibrary(System.java:1047)
    at com.sun.gluegen.runtime.NativeLibLoader.loadLibraryInternal(NativeLibLoader.java:102)
    at com.sun.gluegen.runtime.NativeLibLoader.access$000(NativeLibLoader.java:51)
    at com.sun.gluegen.runtime.NativeLibLoader$1.run(NativeLibLoader.java:70)
    at java.security.AccessController.doPrivileged(Native Method)
    at com.sun.gluegen.runtime.NativeLibLoader.loadGlueGenRT(NativeLibLoader.java:68)
    at com.sun.gluegen.runtime.NativeLibrary.ensureNativeLibLoaded(NativeLibrary.java:399)
    at com.sun.gluegen.runtime.NativeLibrary.open(NativeLibrary.java:163)
    at com.sun.gluegen.runtime.NativeLibrary.open(NativeLibrary.java:129)
    at com.sun.opengl.impl.x11.DRIHack.begin(DRIHack.java:109)
    at com.sun.opengl.impl.x11.X11GLDrawableFactory.<clinit>(X11GLDrawableFactory.java:99)
    at java.lang.Class.forName0(Native Method)
    at java.lang.Class.forName(Class.java:186)
    at javax.media.opengl.GLDrawableFactory.getFactory(GLDrawableFactory.java:111)
    at javax.media.opengl.GLCanvas.chooseGraphicsConfiguration(GLCanvas.java:520)
    at javax.media.opengl.GLCanvas.<init>(GLCanvas.java:131)
    at javax.media.opengl.GLCanvas.<init>(GLCanvas.java:90)
    at org.jzy3d.plot3d.rendering.canvas.CanvasAWT.<init>(CanvasAWT.java:45)
    at org.jzy3d.plot3d.rendering.canvas.CanvasAWT.<init>(CanvasAWT.java:40)
    at org.jzy3d.chart.Chart.initializeCanvas(Chart.java:65)
    at org.jzy3d.chart.Chart.<init>(Chart.java:56)
    at org.jzy3d.chart.Chart.<init>(Chart.java:39)
[/PHP]

---

### Post by dwhitney67 on 2011-08-13
Libraries are prefaced with "lib", thus the file you seek should be called "libgluegen-rt.so".

Try looking for it in the obvious places (/usr/lib or /usr/lib64 or somewhere under /usr).

If it is located in a directory that is not in the dynamic linker (ldconfig) cache, then you either a) need to add it, or b) define LD_LIBRARY_PATH to include the directory path of the library.

I've had similar issue that you are describing with a project I support and that is setup with NetBeans.  One thing that dismayed me was that even after setting up LD_LIBRARY_PATH, the setting was not picked up by NetBeans when I launched it via the Gnome Applications->Programming menu option.  I had to resort to launching NetBeans via the command line.

---

### Post by Kentucky88 on 2011-08-13
I didn't know that all libraries were pre-faced with lib.  Makes sense.  I found libgluegen-rt located at /usr/lib64/jni.  I got my project working after adding that path to Native Library Locations under JRE System Library in Eclipse.  I have not used Netbeans in a long time, but in Eclipse, you select the Build-Path Configuration Menu, go to Libraries, then under JRE System Library, add /usr/lib64/jni.  I think you can also include it by going under Run Configurations and then adding the library path under VM Arguments.  Eclipse is usually pretty good at figuring out where the necessary resources are or alerting the programmer if something is missing.  However, when it comes to native shared libraries, things fall apart.

Jzy3d is a pretty cool project, a very powerful data visualization tool.

---

