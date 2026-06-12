---
title: "librxtxSerial64.so problem with arduino on Ubuntu 12.04.2 64 bit on AMD lapop"
date: 2013-06-26
forum: New to Ubuntu
---

### Post by msousa on 2013-06-26
Hi,

I have a 64bit AMD machine with Ubuntu 12.04.2 installed. I've installed and built arduino-1.0.5. When trying to run I get the following complaint about librxtxSerial64.so (I've tried this with the 32 bit version also and it behaved the same):

The following is the exception from the terminal:
```

linux64-run:
     [exec] java.lang.UnsatisfiedLinkError:  /home/mike/Downloads/arduino-1.0.5/Arduino/build/linux/work/lib/librxtxSerial64.so:   /home/mike/Downloads/arduino-1.0.5/Arduino/build/linux/work/lib/librxtxSerial64.so:  wrong ELF class: ELFCLASS64 (Possible cause: architecture word width  mismatch) thrown while loading gnu.io.RXTXCommDriver
     [exec]  Exception in thread "main" java.lang.UnsatisfiedLinkError:  /home/mike/Downloads/arduino-1.0.5/Arduino/build/linux/work/lib/librxtxSerial64.so:   /home/mike/Downloads/arduino-1.0.5/Arduino/build/linux/work/lib/librxtxSerial64.so:  wrong ELF class: ELFCLASS64 (Possible cause: architecture word width  mismatch)
     [exec]    at java.lang.ClassLoader$NativeLibrary.load(Native Method)
     [exec]    at java.lang.ClassLoader.loadLibrary0(Unknown Source)
     [exec]    at java.lang.ClassLoader.loadLibrary(Unknown Source)
     [exec]    at java.lang.Runtime.loadLibrary0(Unknown Source)
     [exec]    at java.lang.System.loadLibrary(Unknown Source)
     [exec]    at gnu.io.CommPortIdentifier.<clinit>(CommPortIdentifier.java:83)
     [exec]    at processing.app.Editor.populateSerialMenu(Editor.java:962)
     [exec]    at processing.app.Editor.buildToolsMenu(Editor.java:691)
     [exec]    at processing.app.Editor.buildMenuBar(Editor.java:476)
     [exec]    at processing.app.Editor.<init>(Editor.java:205)
     [exec]    at processing.app.Base.handleOpen(Base.java:705)
     [exec]    at processing.app.Base.handleOpen(Base.java:670)
     [exec]    at processing.app.Base.handleNew(Base.java:566)
     [exec]    at processing.app.Base.<init>(Base.java:306)
     [exec]    at processing.app.Base.main(Base.java:195)

```

I followed the build commands from here:
[http://code.google.com/p/arduino/wiki/BuildingArduino](http://code.google.com/p/arduino/wiki/BuildingArduino)

Any ideas what I can do about librxtxSerial?

Thanks...

---

### Post by msousa on 2013-06-29
Those arduino build command are:

```

$ git clone git://github.com/arduino/Arduino.git
$ cd </path/to/arduino/build> // In my case it was ~/Arduino/build
$ ant
$
# if everything went well, you'll have no errors.
$ ant run

```

A pop-up would ask for what directory to use, once that was selected, the above exception (in original post) occurred.

Again, I have a 64bit AMD machine with Ubuntu 12.04.2 installed.

Any help would be appreciated.

Thanks...

---

