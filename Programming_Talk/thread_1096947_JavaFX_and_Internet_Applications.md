---
title: "JavaFX and Internet Applications"
date: 2009-03-15
forum: Programming Talk
---

### Post by pfdevil on 2009-03-15
Hello,

I have checked out JavaFX and was quite disappointed that it isn't available on linux. However that's not my problem with it. I see that JavaFX is advertised for creating "rich internet applications". I quite like java ,but I never really got on the java web applet band wagon.

The reason I don't like java on the web, is the long time it takes to load. Users hates to wait thus they won't wait for a web app to load.

What do you guys think? Should java be used for web app development? What is the best implementation method?

---

### Post by Tomosaur on 2009-03-15
I wouldn't, personally. Perhaps with the right application, the load times wouldn't be so much of a problem (if you're the only one offering that application, or whatever), but generally speaking Java just isn't all that great for that kind of thing.

---

### Post by jespdj on 2009-03-15
This is supposed to get better in the future. Sun is working on making the Java runtime environment modular, which means that if you would go to a page that contains a Java applet, only the core part of the JRE will get loaded into memory, which is much faster than it works until now.

With JavaFX, Sun wants to compete with Adobe Flash, which means that they need to make Java as quick and easy to install and as fast to load as Flash.

The JavaFX SDK will become available for Linux in the future. Currently it isn't because Sun has to make the included video and audio codecs work on Linux. There is a way to install the JavaFX SDK on Linux though (without the codecs), using the Mac OS X version of the SDK. Google for "javafx linux" to find a page with instructions.

I'd say that currently it's too early to use JavaFX for serious web applications. But the idea is good, and I hope it will become a success in the future.

---

