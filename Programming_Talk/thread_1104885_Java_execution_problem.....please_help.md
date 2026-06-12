---
title: "Java execution problem.....please help"
date: 2009-03-24
forum: Programming Talk
---

### Post by mail2vishwas.s on 2009-03-24
Hi,

I'm trying to execute a java program which creates a window using awt

I'm able to compile it....but the problem is that i'm not able to execute it.

I get the following error.


No protocol specified
Exception in thread "main" java.lang.InternalError: Can't connect to X11 window server using ':0.0' as the value of the DISPLAY variable.
        at sun.awt.X11GraphicsEnvironment.initDisplay(Native Method)
        at sun.awt.X11GraphicsEnvironment.access$100(X11GraphicsEnvironment.java:60)
        at sun.awt.X11GraphicsEnvironment$1.run(X11GraphicsEnvironment.java:164)
        at java.security.AccessController.doPrivileged(Native Method)
        at sun.awt.X11GraphicsEnvironment.<clinit>(X11GraphicsEnvironment.java:140)
        at java.lang.Class.forName0(Native Method)
        at java.lang.Class.forName(Class.java:186)
        at java.awt.GraphicsEnvironment.getLocalGraphicsEnvironment(GraphicsEnvironment.java:82)
        at java.awt.Window.init(Window.java:385)
        at java.awt.Window.<init>(Window.java:438)
        at java.awt.Frame.<init>(Frame.java:419)
        at HelloGUI.main(HelloGUI.java:7)






I'd be grateful if you help. :D

---

### Post by men28 on 2009-03-24
I see at the beginning: _sun_.awt.X11Gra...

Are you sure you use Sun's Java?

Please print in the terminal:  
```
java -version
```
and post there.

---

### Post by Zugzwang on 2009-03-24
Such an error typically occurs if you log in remotely using SSH and forget to activate the X-forwarding.

Use the "-Y" or "-X" switch when ssh'ing.
```

ssh -Y user@server

```

---

