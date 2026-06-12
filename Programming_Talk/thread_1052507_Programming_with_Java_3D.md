---
title: "Programming with Java 3D"
date: 2009-01-27
forum: Programming Talk
---

### Post by TheBlackNoodle on 2009-01-27
I'm trying to start programming with Java 3D, but I think I'm having problems with the initial setup. I'm working in Eclipse and have included j3dcore.jar, j3dutils.jar, and vecmath.jar in the build path.

My program is a very simple test from a tutorial:

```

package tests;

import com.sun.j3d.utils.universe.SimpleUniverse;
import com.sun.j3d.utils.geometry.ColorCube;
import javax.media.j3d.BranchGroup;

public class Hello3d {

  public Hello3d()
  {
    SimpleUniverse universe = new SimpleUniverse();
    BranchGroup group = new BranchGroup();
    group.addChild(new ColorCube(0.3));
    universe.getViewingPlatform().setNominalViewingTransform();
    universe.addBranchGraph(group);
  }

  public static void main(String[] args) {
    new Hello3d();
    System.out.println("blah");
  }
}

```

And I get the following exception when it runs:

```

Exception in thread "main" java.lang.NoClassDefFoundError: javax.media.j3d.X11NativeConfigTemplate3D
   at java.lang.Class.initializeClass(libgcj.so.90)
   at java.lang.Class.forName(libgcj.so.90)
   at javax.media.j3d.NativeConfigTemplate3D$1.run(NativeConfigTemplate3D.java:60)
   at java.security.AccessController.doPrivileged(libgcj.so.90)
   at javax.media.j3d.NativeConfigTemplate3D.createNativeConfigTemplate3D(NativeConfigTemplate3D.java:55)
   at javax.media.j3d.NativePipeline.initialize(NativePipeline.java:107)
   at javax.media.j3d.Pipeline.createPipeline(Pipeline.java:151)
   at javax.media.j3d.MasterControl.loadLibraries(MasterControl.java:926)
   at javax.media.j3d.VirtualUniverse.<clinit>(VirtualUniverse.java:280)
   at java.lang.Class.initializeClass(libgcj.so.90)
   at java.lang.Class.initializeClass(libgcj.so.90)
   at tests.Hello3d.<init>(Hello3d.java:11)
   at tests.Hello3d.main(Hello3d.java:19)
Caused by: java.lang.ClassNotFoundException: sun.awt.X11GraphicsDevice not found in gnu.gcj.runtime.SystemClassLoader{urls=[file:/home/max/Dropbox/Projects/Basic Java3D Linux AMD64/,file:/home/max/Dropbox/Projects/Basic Java3D Linux AMD64/Java3D/Linux AMD64/lib/ext/j3dcore.jar,file:/home/max/Dropbox/Projects/Basic Java3D Linux AMD64/Java3D/Linux AMD64/lib/ext/j3dutils.jar,file:/home/max/Dropbox/Projects/Basic Java3D Linux AMD64/Java3D/Linux AMD64/lib/ext/vecmath.jar], parent=gnu.gcj.runtime.ExtensionClassLoader{urls=[], parent=null}}
   at java.net.URLClassLoader.findClass(libgcj.so.90)
   at java.lang.ClassLoader.loadClass(libgcj.so.90)
   at java.lang.ClassLoader.loadClass(libgcj.so.90)
   at java.lang.Class.forName(libgcj.so.90)
   at java.lang.Class.initializeClass(libgcj.so.90)
   ...12 more

```

I installed libgcj via Synaptic but still have the same problem, so I'm unsure how I should proceed. Any ideas?

---

### Post by jespdj on 2009-01-28
> **TheBlackNoodle said:**
> I installed libgcj via Synaptic ...
Argh! Forget about libgcj. Use Sun Java 6, not GNU Java, because GNU Java is a slow, incomplete and incompatible version of Java that you do not want to use. libgcj does not have anything to do with your problem and installing it is not going to solve anything.

> **TheBlackNoodle said:**
> ```
Exception in thread "main" java.lang.NoClassDefFoundError: javax.media.j3d.X11NativeConfigTemplate3D
```
You are missing a JAR file in the classpath. Find out in which JAR file this class is and put it in the classpath.

---

### Post by ufis on 2009-01-28
> **TheBlackNoodle said:**
> ...have included j3dcore.jar, j3dutils.jar, and vecmath.jar in the build path...

I believe you need to install Java3D, and not just put the jars in your build path.

From: [http://download.java.net/media/java3d/builds/release/1.5.2/README-download.html](http://download.java.net/media/java3d/builds/release/1.5.2/README-download.html)
> Preferred method

Developers who wish to develop an application using the Java 3D API are encouraged to download the j3d-1_5_2-XXX.zip file for their platform, and manually install the necessary files into a directory on their local disk. To do this, **unzip the downloaded file, and follow the instructions in the unzipped README.txt file.** 

---

### Post by Kilon on 2009-01-28
> **ufis said:**
> I believe you need to install Java3D, and not just put the jars in your build path.

From: [http://download.java.net/media/java3d/builds/release/1.5.2/README-download.html](http://download.java.net/media/java3d/builds/release/1.5.2/README-download.html)

Why install JAVA3D ? JAVA3D is part of the JAVA platform , so it should be already there. Is this a GNU JAVA specific issue ?

Is GNU JAVA the same as Open JAVA ?

---

### Post by Zugzwang on 2009-01-28
> **Kilon said:**
> Why install JAVA3D ? JAVA3D is part of the JAVA platform , so it should be already there. Is this a GNU JAVA specific issue ?

No, Java3D is a part of the platform that is not installed by default. You need to install it individually.

---

### Post by Kilon on 2009-01-28
> **Zugzwang said:**
> No, Java3D is a part of the platform that is not installed by default. You need to install it individually.


Hmm strange , there is not a distinction in the JAVA for MACOS. There is only one platform and contains all the libraries. However I visited JAVA3d website and says what you are syaing for Windows and Linux. 

> Java 3D 1.3.1 is bundled with Mac OS X 10.4 (Tiger) and is an optional install available from Apple for 10.3.1 or later. Java 3D 1.4 is not available for Mac OS X. 


[http://wiki.java.net/bin/view/Javadesktop/Java3DFAQ](http://wiki.java.net/bin/view/Javadesktop/Java3DFAQ)

Thus my confusion.....

---

### Post by jespdj on 2009-01-28
> **Kilon said:**
> Is GNU JAVA the same as Open JAVA ?
No, GNU Java is not the same as OpenJDK Java.

GNU Java was created a few years back, when Sun Java was still proprietary, and someone wanted a free software implementation of Java.

In 2006 or so, Sun announced that they were going to open source their own Java implementation. The project to make Sun's Java open source is called [OpenJDK](http://openjdk.java.net/). The current version of OpenJDK is almost, but not 100%, identical to Sun Java 6. Sun could not just oepn source their Java 6 like that, because they made use of some third-party components with licences that don't permit publishing the code. Those parts need to be replaced by open source software, which is what people are doing in the OpenJDK project.

OpenJDK Java works well, but is unfortunately not (yet) 100% compatible with Sun Java 6, which causes problems with some Java applets, notably with applets that some banks use on their websites for online banking.

GNU Java has become more or less obsolete since Sun is now working on open sourcing their own Java. GNU Java is an incomplete implementation of Java 1.4 (an old version), and unfortunately it's very slow, because it doesn't contain things like a very sophisticated just-in-time compiler, which Sun Java does have.

Note: The JARs do not have to be only in the **build** path, they must also be in the classpath when you run the program, otherwise you'll get NoClassDefFoundError.

---

### Post by Kilon on 2009-01-28
> **jespdj said:**
> No, GNU Java is not the same as OpenJDK Java.

GNU Java was created a few years back, when Sun Java was still proprietary, and someone wanted a free software implementation of Java.

In 2006 or so, Sun announced that they were going to open source their own Java implementation. The project to make Sun's Java open source is called [OpenJDK](http://openjdk.java.net/). The current version of OpenJDK is almost, but not 100%, identical to Sun Java 6. Sun could not just oepn source their Java 6 like that, because they made use of some third-party components with licences that don't permit publishing the code. Those parts need to be replaced by open source software, which is what people are doing in the OpenJDK project.

OpenJDK Java works well, but is unfortunately not (yet) 100% compatible with Sun Java 6, which causes problems with some Java applets, notably with applets that some banks use on their websites for online banking.

GNU Java has become more or less obsolete since Sun is now working on open sourcing their own Java.

If I wanted a better explanation than this I would have been an idiot. Thanks a lot. I had the privilege to look some of the code that Java open has and It was not so difficult , very interesting stuff.

---

### Post by TheBlackNoodle on 2009-01-28
Wow, thanks for all the replies guys.

With your help, I found out the problem was the JRE that Eclipse was referencing. I had to manually add Sun Java to the list of installed JRE's and make it active for the project.

For anyone with the same problem:

If your versions of java were installed to the default locations, you can find them with ls /usr/lib/jvm. The light blue ones are the symlinks, and I suggest using those...

If your versions aren't installed to the default locations, you can find all versions (and what is currently the default) with sudo update-alternatives --config java.

In Eclipse, I went to Window->Preferences->Java->Installed JREs, clicked Add, and set the JRE Home Directory to /usr/lib/jvm/java-6-sun. I enabled that and disabled gcj. Lo and behold, it runs without an exception now.

---

