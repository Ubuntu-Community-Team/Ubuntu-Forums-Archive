---
title: "Installing Arduino"
date: 2008-11-13
forum: Outdated Tutorials &amp; Tips
---

### Post by parkerhiggins on 2008-11-13
Hello everybody!

I had a little trouble installing the Arduino software on my Intrepid box, and the solution was not intuitive and not on this forum (or, as near as I can tell, anywhere.)  So here are the steps I followed:

First, install the necessary packages.
```
sudo apt-get install sun-java6-jre sun-java6-fonts sun-java6-plugin gcc-avr avr-libc
```
You may also need to remove "brltty", which is a daemon which drives Braille displays.  This is written on the Arduino install page, so I did it, and I didn't see if it would work otherwise.  So, unless you're blind, for good measure:
```
sudo apt-get remove brltty
```

Next you have to download the Arduino program from this page: [http://arduino.cc/en/Main/Software]("http://arduino.cc/en/Main/Software")

Now is where it (might) get tricky.  Unpack the archive you downloaded and go into the directory that creates (arduino-0012, probably) and run the script "arduino".  (./arduino)  I've heard this almost always works, but it didn't for me.  I got a long error message:
```
Exception in thread "main" java.lang.UnsatisfiedLinkError: Can't load library: /usr/lib/jvm/java-6-openjdk/jre/lib/i386/xawt/libmawt.so
	at java.lang.ClassLoader.loadLibrary(ClassLoader.java:1666)
	at java.lang.Runtime.load0(Runtime.java:787)
	at java.lang.System.load(System.java:1022)
	at java.lang.ClassLoader$NativeLibrary.load(Native Method)
	at java.lang.ClassLoader.loadLibrary0(ClassLoader.java:1767)
	at java.lang.ClassLoader.loadLibrary(ClassLoader.java:1684)
	at java.lang.Runtime.loadLibrary0(Runtime.java:840)
	at java.lang.System.loadLibrary(System.java:1047)
	at sun.security.action.LoadLibraryAction.run(LoadLibraryAction.java:67)
	at sun.security.action.LoadLibraryAction.run(LoadLibraryAction.java:47)
	at java.security.AccessController.doPrivileged(Native Method)
	at java.awt.Toolkit.loadLibraries(Toolkit.java:1610)
	at java.awt.Toolkit.<clinit>(Toolkit.java:1632)
	at java.awt.Component.<clinit>(Component.java:568)
	at processing.app.Base.main(Base.java:72)
```

And sure enough, I had no xawt directory!

If you get that also, just run the following command:
```
sudo update-java-alternatives -s java-6-sun
```

That totally cleared up the problem for me, and now it's running like a charm.  Hope that works for you!

---

### Post by Arrowx7 on 2008-11-27
That's awesome, thanks so much for sharing this with us.

I had a problem like this installing Limewire and this fixed it!!

---

### Post by Keen101 on 2008-12-12
This might be of interest too.

[http://ubuntuforums.org/showthread.php?t=949229](http://ubuntuforums.org/showthread.php?t=949229)

This isn't exactly a tutorial, but here is a reply i had a while back where i used openjdk instead of the sun java.

[http://ubuntuforums.org/showthread.php?t=783391](http://ubuntuforums.org/showthread.php?t=783391)

---

### Post by snebtor on 2009-03-06
worked for me right away. Thanks (ubuntu studio 8.10)

---

### Post by WadeH2o on 2009-03-29
Huge Help! I was running Arduino in VISTA which was getting annoying, thank you very much for the help. \\:D/

I'm still a beginer with Linux so bear with me, I have a few questions.

1) I cannot find Arduino in my list of programs from the Applications menu, what's the easiest way to launch it? Is it possible to launch it from Terminal?

2) To find the com port on VISTA I use "Device Manager", is there a better way than to just select the ports one by one until I find the port for Arduino hardware?
[B]
Alright I found the answer to question number one with the link in post #3. [/B]

---

### Post by ghendrix on 2009-04-02
Thanks! The Arduino website says that avr-gcc needs to be updated on Intrepid but that didn't help at all.

---

### Post by binbash on 2009-04-02
works good

---

