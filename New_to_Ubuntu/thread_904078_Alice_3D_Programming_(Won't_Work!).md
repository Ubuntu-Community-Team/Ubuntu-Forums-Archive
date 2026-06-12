---
title: "Alice 3D Programming (Won't Work!)"
date: 2008-08-28
forum: New to Ubuntu
---

### Post by chris062689 on 2008-08-28
I'm taking a college class that requires this, and I really, really don't want to switch back to Windows for this stupid thing...

It's called Alice.
[http://www.alice.org/](http://www.alice.org/)

I am running Ubuntu 8.04 64bit.
This is what happens when I try to run the program:
```
chris@chris-desktop:~/Alice/Required$ ./run-alice
attempting to register mp3 capability... 
Registered succesfully
java.lang.UnsatisfiedLinkError: /home/chris/Alice/Required/jogl/lib/linux-i586/libjogl_drihack.so: /home/chris/Alice/Required/jogl/lib/linux-i586/libjogl_drihack.so: wrong ELF class: ELFCLASS32 (Possible cause: architecture word width mismatch)
	at java.lang.ClassLoader$NativeLibrary.load(Native Method)
	at java.lang.ClassLoader.loadLibrary0(ClassLoader.java:1751)
	at java.lang.ClassLoader.loadLibrary(ClassLoader.java:1676)
	at java.lang.Runtime.loadLibrary0(Runtime.java:823)
	at java.lang.System.loadLibrary(System.java:1030)
	at com.sun.opengl.impl.NativeLibLoader$DefaultAction.loadLibrary(NativeLibLoader.java:78)
	at com.sun.opengl.impl.NativeLibLoader.loadLibrary(NativeLibLoader.java:101)
	at com.sun.opengl.impl.NativeLibLoader.access$100(NativeLibLoader.java:47)
	at com.sun.opengl.impl.NativeLibLoader$3.run(NativeLibLoader.java:141)
	at java.security.AccessController.doPrivileged(Native Method)
	at com.sun.opengl.impl.NativeLibLoader.loadDRIHack(NativeLibLoader.java:139)
	at com.sun.opengl.impl.x11.DRIHack.begin(DRIHack.java:105)
	at com.sun.opengl.impl.x11.X11GLDrawableFactory.<clinit>(X11GLDrawableFactory.java:66)
	at java.lang.Class.forName0(Native Method)
	at java.lang.Class.forName(Class.java:169)
	at javax.media.opengl.GLDrawableFactory.getFactory(GLDrawableFactory.java:111)
	at javax.media.opengl.GLCanvas.<init>(GLCanvas.java:113)
	at javax.media.opengl.GLCanvas.<init>(GLCanvas.java:82)
	at javax.media.opengl.GLCanvas.<init>(GLCanvas.java:75)
	at edu.cmu.cs.stage3.alice.scenegraph.renderer.joglrenderer.OnscreenRenderTarget.getAWTComponent(OnscreenRenderTarget.java:57)
	at edu.cmu.cs.stage3.alice.authoringtool.util.RenderTargetPickManipulator.setRenderTarget(RenderTargetPickManipulator.java:74)
	at edu.cmu.cs.stage3.alice.authoringtool.util.RenderTargetPickManipulator.<init>(RenderTargetPickManipulator.java:45)
	at edu.cmu.cs.stage3.alice.authoringtool.util.RenderTargetMultiManipulator.<init>(RenderTargetMultiManipulator.java:33)
	at edu.cmu.cs.stage3.alice.authoringtool.editors.sceneeditor.CameraViewPanel.renderInit(CameraViewPanel.java:867)
	at edu.cmu.cs.stage3.alice.authoringtool.editors.sceneeditor.SceneEditor.setAuthoringTool(SceneEditor.java:215)
	at edu.cmu.cs.stage3.alice.authoringtool.JAliceFrame.guiInit(JAliceFrame.java:157)
	at edu.cmu.cs.stage3.alice.authoringtool.JAliceFrame.<init>(JAliceFrame.java:71)
	at edu.cmu.cs.stage3.alice.authoringtool.AuthoringTool.mainInit(AuthoringTool.java:456)
	at edu.cmu.cs.stage3.alice.authoringtool.AuthoringTool.<init>(AuthoringTool.java:408)
	at edu.cmu.cs.stage3.alice.authoringtool.JAlice.main(JAlice.java:131)


```
Can someone please help me?  :(

---

### Post by chris062689 on 2008-08-28
People are saying using Java 1.4 is making it a lot more stable, but how the heck do I get that version on my machine?  I tried the installer from Sun's site, but I got this..

```

Do you agree to the above license terms? [yes or no] 
yes
Unpacking...
Checksumming...
0
0
Extracting...
./j2re-1_4_2_18-linux-i586.bin: 383: ./install.sfx.18980: not found
Done.

```

---

### Post by chris062689 on 2008-08-29
Sorry to bump this post, but I really need help getting this working for school.  I don't want to switch back to Windows! :(

---

### Post by ellgor on 2008-08-29
Hi,

There used to be a package called j2re-1.4(Blackdown-edition) in the repositries, I think it was not continued in the 8.04 edition, I say this because I'm using Gutsy at the minute and its still in this repositry.
There should be an option in synaptic to use backports (again you might have to enquire further) but if there is you will know what to look for, it self loads, apart from agreeing to the licence, and hopefully this will help you.

Regards, Ellgor.

---

### Post by gandaran on 2008-08-29
all sun java packages only install/work on 32-bit ubuntu, check synaptic package manager, I don't know, (I use 32-bit), but there could be there a special prepared sun-java6-jre to work on 64-bits systems.

---

### Post by fudje on 2008-08-31
It's not the JRE that's the problem, it's the supplied libjogl libraries in Alice.  I'm currently having the same problems, and it is difficult to work around because more recent versions of libjogl (eg. the one in the repositories) don't *need* the drihack library, thus don't have it.

What you need to do, then, is download the file jogl-1_0_0-linux-amd64.zip from [jogl.dev.java.net old releases (click)](https://jogl.dev.java.net/servlets/ProjectDocumentList?folderID=5971&expandFolder=5971&folderID=271), unzip it, and copy all the .so files (libjogl_awt.so, libjogl_cg.so, libjogl_drihack.so, and libjogl.so) to Alice/Required/jogl/lib/linux-i586/ (in your case /home/chris/Alice/Required/jogl/lib/linux-i586/).  You should then be able to start Alice normally with the run-alice script.  You may get some XCB locking assertion failures on startup, but they don't seem to affect the program.

Cheers,
fudje

---

### Post by chris062689 on 2008-08-31
That worked!
Thank you so much!

---

### Post by fedex1993 on 2008-09-01
i am currently taking alice too but i didn't like i think hard core codeing is better than using 3d programming

---

### Post by Lanrat on 2008-09-16
Thanks, I am also taking a class on Alice and this had helped me.

---

### Post by Deborah K. Mathews on 2008-12-29
I'm on an AMD 64-bit machine, and I just upgraded to Intrepid Ibex from Hardy Heron.  When I open a world, it doesn't show in the window until after I've played the world.  When I play the world, I get dialog boxes and sound, but there is no movement of the 3-D objects.

---

### Post by Deborah K. Mathews on 2008-12-29
Now it starts Alice, but when I open a world it gives me a brief glimpse of the scene in the world window, and then it turns black, and the rest of the screen blanks out.

When I run it in the terminal, I get a bunch of error messages before Alice starts, and no further error messages when I attempt to start a world:

attempting to register mp3 capability... 
Registered succesfully
*sys-package-mgr*: processing modified jar, '/usr/lib/jvm/java-1.5.0-sun-1.5.0.16/jre/lib/rt.jar'
*sys-package-mgr*: can't write cache file for '/usr/lib/jvm/java-1.5.0-sun-1.5.0.16/jre/lib/rt.jar'
*sys-package-mgr*: processing modified jar, '/usr/lib/jvm/java-1.5.0-sun-1.5.0.16/jre/lib/jsse.jar'
*sys-package-mgr*: can't write cache file for '/usr/lib/jvm/java-1.5.0-sun-1.5.0.16/jre/lib/jsse.jar'
*sys-package-mgr*: processing modified jar, '/usr/lib/jvm/java-1.5.0-sun-1.5.0.16/jre/lib/jce.jar'
*sys-package-mgr*: can't write cache file for '/usr/lib/jvm/java-1.5.0-sun-1.5.0.16/jre/lib/jce.jar'
*sys-package-mgr*: processing modified jar, '/usr/lib/jvm/java-1.5.0-sun-1.5.0.16/jre/lib/charsets.jar'
*sys-package-mgr*: can't write cache file for '/usr/lib/jvm/java-1.5.0-sun-1.5.0.16/jre/lib/charsets.jar'
*sys-package-mgr*: processing modified jar, '/usr/lib/jvm/java-1.5.0-sun-1.5.0.16/jre/lib/ext/dnsns.jar'
*sys-package-mgr*: can't write cache file for '/usr/lib/jvm/java-1.5.0-sun-1.5.0.16/jre/lib/ext/dnsns.jar'
*sys-package-mgr*: processing modified jar, '/usr/lib/jvm/java-1.5.0-sun-1.5.0.16/jre/lib/ext/sunjce_provider.jar'
*sys-package-mgr*: can't write cache file for '/usr/lib/jvm/java-1.5.0-sun-1.5.0.16/jre/lib/ext/sunjce_provider.jar'
*sys-package-mgr*: processing modified jar, '/usr/lib/jvm/java-1.5.0-sun-1.5.0.16/jre/lib/ext/localedata.jar'
*sys-package-mgr*: can't write cache file for '/usr/lib/jvm/java-1.5.0-sun-1.5.0.16/jre/lib/ext/localedata.jar'
*sys-package-mgr*: processing modified jar, '/usr/lib/jvm/java-1.5.0-sun-1.5.0.16/jre/lib/ext/sunpkcs11.jar'
*sys-package-mgr*: can't write cache file for '/usr/lib/jvm/java-1.5.0-sun-1.5.0.16/jre/lib/ext/sunpkcs11.jar'
Locking assertion failure.  Backtrace:
#0 /usr/lib/libxcb-xlib.so.0 [0x7fb78d6f99fc]
#1 /usr/lib/libxcb-xlib.so.0(xcb_xlib_unlock+0x24) [0x7fb78d6f9ab4]
#2 /usr/lib/libX11.so.6(_XReply+0x268) [0x7fb78db47698]
#3 /usr/lib/jvm/java-1.5.0-sun-1.5.0.16/jre/lib/amd64/xawt/libmawt.so [0x7fb78e053d7b]
#4 /usr/lib/jvm/java-1.5.0-sun-1.5.0.16/jre/lib/amd64/xawt/libmawt.so [0x7fb78e040e9c]
#5 /usr/lib/jvm/java-1.5.0-sun-1.5.0.16/jre/lib/amd64/xawt/libmawt.so [0x7fb78e040ffe]
#6 /usr/lib/jvm/java-1.5.0-sun-1.5.0.16/jre/lib/amd64/xawt/libmawt.so(Java_sun_awt_X11GraphicsEnvironment_initDisplay+0x9) [0x7fb78e0411c9]
#7 [0x7fb7b6360f7b]
Locking assertion failure.  Backtrace:
#0 /usr/lib/libxcb-xlib.so.0 [0x7fb78d6f99fc]
#1 /usr/lib/libxcb-xlib.so.0(xcb_xlib_lock+0x17) [0x7fb78d6f9b77]
#2 /usr/lib/libX11.so.6 [0x7fb78db468c0]
#3 /usr/lib/libX11.so.6(XGetVisualInfo+0x2e) [0x7fb78db3d08e]
#4 /usr/lib/jvm/java-1.5.0-sun-1.5.0.16/jre/lib/amd64/xawt/libmawt.so [0x7fb78e0401f7]
#5 /usr/lib/jvm/java-1.5.0-sun-1.5.0.16/jre/lib/amd64/xawt/libmawt.so [0x7fb78e040431]
#6 /usr/lib/jvm/java-1.5.0-sun-1.5.0.16/jre/lib/amd64/xawt/libmawt.so [0x7fb78e041099]
#7 /usr/lib/jvm/java-1.5.0-sun-1.5.0.16/jre/lib/amd64/xawt/libmawt.so(Java_sun_awt_X11GraphicsEnvironment_initDisplay+0x9) [0x7fb78e0411c9]
#8 [0x7fb7b6360f7b]

Any help would be much appreciated!

---

### Post by Deborah K. Mathews on 2008-12-31
Well, a friend of mine also running Intrepid Ibex on a 64-bit machine is able to run Alice no problem.  I installed Hardy Heron as a second operating system on my machine, and Alice worked fine.  I then enabled the proprietary ATI driver, and it didn't work.  Then I disabled that driver and it worked again.  I was hoping disabling the driver would fix the problems in Intrepid Ibex, but it made no difference.  Nonetheless, since my friend is having no problems whatsoever, and since the driver for my video card did affect its running in Hardy Heron, it is possible that the problem has to do with my Radeon HD 3200 card and whatever drivers are running it.

---

### Post by Deborah K. Mathews on 2008-12-31
My friend just remembered that he switched to a 32-bit install a few weeks ago, so it hasn't been shown after all that Alice will run on 64-bit Intrepid Ibex.

---

### Post by goldenfleece on 2009-01-25
fudje, I tried your fix and it started an Alice gui for just a moment, then disappeared, and then gave me some error info in terminal (below).  I'm hoping for some good advice....anyone, anyone?

 An unexpected error has been detected by Java Runtime Environment:
#
#  SIGSEGV (0xb) at pc=0x00007fb7384ee330, pid=8100, tid=1108687184
#
# Java VM: OpenJDK 64-Bit Server VM (1.6.0_0-b11 mixed mode linux-amd64)
# Problematic frame:
# C  [libc.so.6+0x7c330]  memset+0x60
#
# The crash happened outside the Java Virtual Machine in native code.
# See problematic frame for where to report the bug.
#
./run-alice: line 1:  8100 Aborted                 java -classpath ./gnu/getopt-1.0.7.jar:./jython-2.1/jython.jar:./lib/alice.jar:./jogl/lib/jogl.jar:./xerces-2_6_2/resolver.jar:./vecmath/lib/ext/vecmath.jar:./xerces-2_6_2/xercesImpl.jar:./xerces-2_6_2/xml-apis.jar:./xerces-2_6_2/xmlParserAPIs.jar:./JMF-2.1.1e/lib/customizer.jar:./JMF-2.1.1e/lib/jmf.jar:./JMF-2.1.1e/lib/mediaplayer.jar:./JMF-2.1.1e/lib/multiplayer.jar:./mp3/lib/ext/mp3plugin.jar -Dpython.home=./jython-2.1 -Djava.library.path=./jogl/lib/linux-i586 -Xincgc -Xmx512m -Dalice.useJavaBasedSplashScreen=false edu.cmu.cs.stage3.alice.authoringtool.JAlice -o -e

---

