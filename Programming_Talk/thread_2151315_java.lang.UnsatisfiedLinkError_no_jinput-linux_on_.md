---
title: "java.lang.UnsatisfiedLinkError: no jinput-linux on Ubuntu 12.04LTS"
date: 2013-06-04
forum: Programming Talk
---

### Post by indarkness on 2013-06-04
Hello, 

I'm having some issues with a java project in which I use a gamepad controller, thrustmaster firestorm dual analog 3 (usb), under ubuntu 12.04LTS. I know the controller works under ubuntu since I can calibrate and test it. The problem lies on running the jar since I get the following error:

```
    un 04, 2013 9:39:42 AM net.java.games.input.ControllerEnvironment log
    INFO: Failed to load library: no jinput-linux in java.library.path
    
    java.lang.UnsatisfiedLinkError: no jinput-linux in java.library.path
        at java.lang.ClassLoader.loadLibrary(ClassLoader.java:1856)
        at java.lang.Runtime.loadLibrary0(Runtime.java:845)
        at java.lang.System.loadLibrary(System.java:1084)
        at net.java.games.input.LinuxEnvironmentPlugin$1.run(LinuxEnvironmentPlugin.java:69)
        at java.security.AccessController.doPrivileged(Native Method)
        at net.java.games.input.LinuxEnvironmentPlugin.loadLibrary(LinuxEnvironmentPlugin.java:61)
        at net.java.games.input.LinuxEnvironmentPlugin.<clinit>(LinuxEnvironmentPlugin.java:102)
        at java.lang.Class.forName0(Native Method)
        at java.lang.Class.forName(Class.java:188)
        at net.java.games.input.DefaultControllerEnvironment.getControllers(DefaultControllerEnvironment.java:159)
        at com.codeminders.ardrone.controllers.ThrustmasterController.initGamepad(ThrustmasterController.java:88)
        at com.codeminders.ardrone.controllers.ThrustmasterController.getGamepad(ThrustmasterController.java:79)
        at com.codeminders.controltower.ControlTower.initController(ControlTower.java:114)
        at com.codeminders.controltower.ControlTower.<init>(ControlTower.java:90)
        at com.codeminders.controltower.ControlTower.main(ControlTower.java:591)
    Jun 04, 2013 9:39:42 AM net.java.games.input.ControllerEnvironment log
    INFO: net.java.games.input.LinuxEnvironmentPlugin is not supported
    
    No gamepad found!
    No suitable controller found! Control disabled
    Connecting to the drone
    Using command port: 1500
```

I have created the .jar artifact with IDEA, and I think I have included all the libraries in the .jar, but even so, I get that error. I have also tried to execute my .jar like this

```
    java -jar javadrone2.jar -Djava.library.path=/usr/li/libjinput.so
```

But with the same output... I believe that I have installed the jinput library, because if I type
```

    :$ locate jinput
    ...
    /usr/lib/jni/libjinput.so
    /usr/share/doc/libjinput-java
    /usr/share/doc/libjinput-jni
    ...
```

What can I do to run my .jar??

Any help will be appreciated!

Thanks in advance!

---

### Post by slickymaster on 2013-06-04
[Set up JInput API and Library for Java Development on Mac OS X or Linux Platform]("http://yaolddawg.blogspot.pt/2011/08/configure-open-source-controller-jinput.html")

---

### Post by indarkness on 2013-06-04
> **slickymaster said:**
> [Set up JInput API and Library for Java Development on Mac OS X or Linux Platform]("http://yaolddawg.blogspot.pt/2011/08/configure-open-source-controller-jinput.html")

Thanks for your reply!

I have already tried that link, but my issue is that I'm trying to execute the .jar I have created, in which the missing library seems to be included...

---

### Post by Leuchten on 2013-06-05
You can point java at the native lib manually like this: java -Djava.library.path=/usr/lib/jni -jar yourJar.jar. If that doesn't work, I'm at a loss.

---

