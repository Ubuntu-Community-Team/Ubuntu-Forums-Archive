---
title: "Cannot build game from source"
date: 2013-04-04
forum: Packaging and Compiling Programs
---

### Post by TheManno1 on 2013-04-04
[Ubuntu studio ]("https://github.com/jubilee145/APFG")[http://ubuntustudio.org/](http://ubuntustudio.org/) 12.04 64 bit.

Here is the Game
[https://github.com/jubilee145/APFG](https://github.com/jubilee145/APFG)

Here is the issue
[https://github.com/jubilee145/APFG/issues/14](https://github.com/jubilee145/APFG/issues/14)
```

john@john-Aspire-5742:~/Downloads/APFG-master$ ant build.xml
Buildfile: /home/john/Downloads/APFG-master/build.xml

BUILD FAILED
Target "build.xml" does not exist in the project "Compile and run". 

Total time: 1 second
john@john-Aspire-5742:~/Downloads/APFG-master$ 


john@john-Aspire-5742:~/Downloads/APFG-master$ ant compile build.xml
Buildfile: /home/john/Downloads/APFG-master/build.xml

compile:
     [echo] Compile and run: /home/john/Downloads/APFG-master/build.xml

BUILD FAILED
/home/john/Downloads/APFG-master/build.xml:18: destination directory "/home/john/Downloads/APFG-master/bin" does not exist or is not a directory

Total time: 1 second
john@john-Aspire-5742:~/Downloads/APFG-master$ 

john@john-Aspire-5742:~/Downloads/APFG-master$ ant run  build.xml
Buildfile: /home/john/Downloads/APFG-master/build.xml

compile:
     [echo] Compile and run: /home/john/Downloads/APFG-master/build.xml

BUILD FAILED
/home/john/Downloads/APFG-master/build.xml:18: destination directory "/home/john/Downloads/APFG-master/bin" does not exist or is not a directory

Total time: 1 second
john@john-Aspire-5742:~/Downloads/APFG-master$
```

---

### Post by oldos2er on 2013-04-04
Moved to Packaging & Compiling Programs.

---

### Post by TheManno1 on 2013-04-07
```

john@john-Aspire-5742:~/Downloads/APFG-master$ ant
Buildfile: /home/john/Downloads/APFG-master/build.xml

compile:
     [echo] Compile and run: /home/john/Downloads/APFG-master/build.xml

run:
     [java] Mon Apr 08 04:14:43 MSK 2013 INFO:Slick Build #261
     [java] Mon Apr 08 04:14:43 MSK 2013 INFO:LWJGL Version: 2.8.5
     [java] Mon Apr 08 04:14:43 MSK 2013 INFO:OriginalDisplayMode: 1366 x 768 x 24 @60Hz
     [java] Mon Apr 08 04:14:43 MSK 2013 INFO:TargetDisplayMode: 1280 x 764 x 0 @0Hz
     [java] Mon Apr 08 04:14:43 MSK 2013 INFO:Starting display 1280x764
     [java] Mon Apr 08 04:14:43 MSK 2013 INFO:Use Java PNG Loader = true
     [java] Mon Apr 08 04:14:43 MSK 2013 INFO:Controllers not available
     [java] Exception in thread "main" java.lang.RuntimeException: Resource not found: assets/stage/images/bgTestObject.png
     [java]     at org.newdawn.slick.util.ResourceLoader.getResourceAsStream(ResourceLoader.java:69)
     [java]     at org.newdawn.slick.opengl.InternalTextureLoader.getTexture(InternalTextureLoader.java:273)
     [java]     at org.newdawn.slick.Image.<init>(Image.java:270)
     [java]     at org.newdawn.slick.Image.<init>(Image.java:244)
     [java]     at org.newdawn.slick.Image.<init>(Image.java:232)
     [java]     at org.newdawn.slick.Image.<init>(Image.java:198)
     [java]     at stage.Stage.<init>(Unknown Source)
     [java]     at gameState.Fight.init(Unknown Source)
     [java]     at org.newdawn.slick.state.StateBasedGame.init(StateBasedGame.java:177)
     [java]     at org.newdawn.slick.AppGameContainer.setup(AppGameContainer.java:433)
     [java]     at org.newdawn.slick.AppGameContainer.start(AppGameContainer.java:357)
     [java]     at svb.Main.main(Unknown Source)

BUILD FAILED
/home/john/Downloads/APFG-master/build.xml:11: Java returned: 1
```

---

