---
title: "Webcam capture with JMF"
date: 2006-01-17
forum: Programming Talk
---

### Post by profox on 2006-01-17
I'm trying to capture my webcam and save the capture as a png image. I installed JMF on my ubuntu machine, added the classpath etc. JMStudio is working great. i can capture my webcam.

but when i'm trying the same with my own program it doesn't work. here some code:

```

CaptureDeviceInfo deviceInfo = CaptureDeviceManager.getDevice("v4l:VideoCam Messenger sn9c101 Ov76:0");
MediaLocator mdl = new MediaLocator("v4l://0");

Player player = null; 
try {
        player = Manager.createRealizedPlayer(mdl);
} catch (IOException ioe ) {
        System.out.println("Error: " + ioe);
}
player.start();

```

when i run the program, he's show's me every format the webcam supports like:

> 
Trying 4 320 240
Format is RGB, 320x240, Length=230400, 24-bit, Masks=3:2:1, PixelStride=3, LineStride=960


and at the end he crashes with;
> 
Exception on commit = java.io.IOException: Can't find registry file
java.io.IOException: java.lang.Error: Couldn't initialize capture device
java.io.IOException: java.lang.Error: Couldn't initialize capture device
Exception in thread "main" javax.media.NoPlayerException: Error instantiating cl ass: com.sun.media.protocol.v4l.DataSource : java.io.IOException: java.lang.Erro r: Couldn't initialize capture device
        at javax.media.Manager.createPlayerForContent(Manager.java:1362)
        at javax.media.Manager.createPlayer(Manager.java:417)
        at javax.media.Manager.createRealizedPlayer(Manager.java:553)
        at FrameGrab.main(FrameGrab.java:22)


when i'm trying some other code:

```

CaptureDeviceInfo deviceInfo = CaptureDeviceManager.getDevice("v4l:VideoCam Messenger sn9c101 Ov76:0");
        
Player player = null;        
try {
        player = Manager.createRealizedPlayer(deviceInfo.getLocator());
} catch (IOException ioe ) {
      	System.out.println("Error: " + ioe);
}
player.start();

```

he quit's with the following error (immediately after i start the program):
> 
Exception in thread "main" java.lang.NullPointerException
        at FrameGrab.main(FrameGrab.java:21)


and i have realy no id why, and how to solve this problem. the device name's are 100% ok, i copied them from JMF Registry. And i tried more than once to detect new capture devices. Why is my program not working, but JMStudio is working fine?

---

### Post by scottpreston on 2006-06-27
Any luck with this? I have the same problem with my "write once" "run anywhere" code.

Works fine in XP, but UBUNTU does not work.

---

### Post by desertsystem on 2006-09-20
Had the same issue with JMF on ununtu... ie jmstudio worked fine but not my own application.

I managed to solve this issue by adding these lines to /etc/bash.bashrc

LD_LIBRARY_PATH=$LD_LIBRARY_PATH:$JMFHOME/lib:$JAVA_HOME/jre/lib/i386:$JAVA_HOME/jre/lib/i386/client
export LD_LIBRARY_PATH

---

### Post by bazz-dee on 2007-03-08
which java version did u use?
cause with java 6 it wont help adding these lines to /etc/bash.bashrc

---

### Post by fcsa on 2008-03-04
same problem over here?
anybody found the solution?

---

### Post by r0b0h0b0 on 2008-06-27
/me joins the queue

FREE TO GOOD HOME:
79 young, healthy , spayed/neutered, inoculated, pedigree breed, caught-and-handled little NullPointerExceptions. Harmless, very cute. Good with kids.

---

