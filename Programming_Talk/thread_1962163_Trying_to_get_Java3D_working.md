---
title: "Trying to get Java3D working"
date: 2012-04-20
forum: Programming Talk
---

### Post by schievelbein on 2012-04-20
I have installed the latest Java according to the stickies.
I can run the Helloworld included and it runs fine, so JAVA is installed correctly.  The problem is with Java3D, I have installed it, but I do not think that the ClassPath is set correctly or something.I am trying to run the following Hello3d.java program and get the error that follows.  Can anyone give me any idea of what to do to correct this?  What commands should I run to verify Classpath and other settings?

```

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
public static void main( String[] args ) {
   new Hello3d();
}
} // end of class Hello3d

```

[OUTPUT]
$ javac Hello3d.java
Hello3d.java:1: package com.sun.j3d.utils.universe does not exist
import com.sun.j3d.utils.universe.SimpleUniverse;
                                 ^
Hello3d.java:3: package com.sun.j3d.utils.geometry does not exist
import com.sun.j3d.utils.geometry.ColorCube;
                                 ^
Hello3d.java:5: package javax.media.j3d does not exist
import javax.media.j3d.BranchGroup;
                      ^
Hello3d.java:13: cannot find symbol
symbol  : class SimpleUniverse
location: class Hello3d
   SimpleUniverse universe = new SimpleUniverse();
   ^
Hello3d.java:13: cannot find symbol
symbol  : class SimpleUniverse
location: class Hello3d
   SimpleUniverse universe = new SimpleUniverse();
                                 ^
Hello3d.java:15: cannot find symbol
symbol  : class BranchGroup
location: class Hello3d
   BranchGroup group = new BranchGroup();
   ^
Hello3d.java:15: cannot find symbol
symbol  : class BranchGroup
location: class Hello3d
   BranchGroup group = new BranchGroup();
                           ^
Hello3d.java:17: cannot find symbol
symbol  : class ColorCube
location: class Hello3d
   group.addChild(new ColorCube(0.3));
                      ^
8 errors

[/OUTPUT]

---

### Post by schievelbein on 2012-04-20
UPDATE
I was able to get the program to compile using:
```

javac -cp ./lib/ext/j3dutils.jar:./lib/ext/j3dcore.jar:./lib/ext/vecmath.jar Hello3d.java

```

I understand that I need to have them in my Classpath, where do I copy these Java3D files where I can use them in all my programs, or how to I change the global classpath?

---

### Post by t1497f35 on 2012-04-20
Afaik Java3D is an old project that never took off and is effectively dead, I suggest [this one]("http://jogamp.org/").

---

