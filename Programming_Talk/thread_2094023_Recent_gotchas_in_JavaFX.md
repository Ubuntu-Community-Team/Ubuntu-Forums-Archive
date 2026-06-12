---
title: "Recent gotchas in JavaFX"
date: 2012-12-12
forum: Programming Talk
---

### Post by Unterseeboot_234 on 2012-12-12
I have been following JavaFX development since version 1.1 which included sometimes required downloading the Mac .jar to get functionality on Linux. The promise is that a working version of FX on Ubuntu as the Linux platform.

NetBeans sent out an announcement for Linux support in the Fall 2012 for JavaFX 2.2 requiring JavaSE 7.0_update6. (Java SE6 reaches its end-of-life cycle in Feb. 2013. JavaFX 2.2 will not support FX-script and instead you should use Scala or Groovy.

The priority for FX releases has been Windows, then Mac and Linux is an afterthought. Basically, Windows and Mac have an installed video player and Linux has a polyglut of choices. The Linux version of JavaFX excludes animation APIs and non-decorated Windows. The other versions of JavaFX can display any shape on the monitor as a Frame.

The JavaSE 7 installer was the surprise. The script finds every SDK on my Ubuntu. You get constant warnings if you run any JRE plug-in < JRE7. To run JavaFX every other JRE has to be deleted. FireFox warns repeatedly to turn off JRE7.

What got me was SE7 installer located every other FX project folder on my machine and changed the linked JRE plug-in to JRE7. All of my earlier code with JavaFX will not run.

The previous Java SDKs used to include a /demo folder full of applets and Graphics2D examples. Those got deleted during all the updates for SDK6.

But, here's the really bitter part. JavaFX now requires a GPU card with 3D onboard acceleration. FX is supposed to use BufferedImage if the GPU doesn't have 3D acceleration. Previously compiled code done on another box will run on my box. I can not compile and run a JavaFX code project that I coded. 

JavaFX 2.2 makes all the old FX textbooks obsolete. And, the plan is to replace Swing with JavaFX.

The only bright spot for the future of FX is the promise of cross-platform and multiple-hardware. Supposedly, the same FX app would run on a web page. Drag the icon from the web page to the Desktop and the app runs as an application. Upload the icon to a mobile device with JRE and said same app runs again.

But, we're a long way off from the promises and I wonder if Oracle might be running out of time.

---

### Post by slickymaster on 2012-12-12
You're right Unterseeboot_234, Oracle's behavior regarding JavaFX's Linux integration has been at least incomprehensible, not to say shameful.

The last official position from Oracle I knew of on JavaFX, was in a [interview with Richard Bair]("http://www.infoq.com/news/2011/03/jfx2ea"), the architect for client software at Oracle that confirms exactly what you explain in your post. 
According to him JavaFX won't be distributed in Linux distributions.

Why is Oracle now favouring Windows over Linux?
Both JavaME SDK 3.0 and JavaFX 2.0, as far as I konw, are unsupported on Linux. This is definitely not the Sun I once knew...

Linux may not be the widest deployed platform for users, but for developers? It's developers who are going to keep Oracle's technologies alive.

---

### Post by slickymaster on 2012-12-12
In case there is anyone interested, here's a tutorial on [Hacking JavaFX Scene Builder to Work on Linux]("http://gautamk.heroku.com/blog/2012/05/05/hacking-javafx-scene-builder-to-work-on-linux").

Don't know if it works (haven't personally tried it out), but worth a try. At least I will.

---

### Post by bird1500 on 2012-12-14
> (...) The only bright spot for the future of FX is the promise of  cross-platform and multiple-hardware. Supposedly, the same FX app would  run on a web page. Drag the icon from the web page to the Desktop and  the app runs as an application. Upload the icon to a mobile device with  JRE and said same app runs again. (...)Won't happen cause it's impossible.
Mobiles:
Android - its Java is a different beast and requiring the clients to install a custom JRE isn't practical.
iPhone - Java is forbidden, like flash.

Desktop:
Linux - it's too diverse, even the sys tray, the task bar, they're all different on unity/gnome/kde/whatever with toolkits like gtk/qt/clutter/nux with their own logic and settings.
Mac - is happy with its own solutions (cocoa & objective c).
Windows - too sophisticated, from XP which is still widely used to win8 which is weird and favors HTML5.

Currently there's no  smooth, efficient, GPU-oriented cross-platform solution, and probably can't be, it's hard to find a good lowest common denominator, Flash tried and stepped back.
The best one is probably Qt.
If you don't do Java(FX) for a living I'd suggest using a compiled/native solution, like C++/Qt, which afaik runs decently on windows and macs too.

But JavaFX is pretty much a dead duck, Oracle can't replace Swing with it cause Oracle is afraid to break backward compatibility even with applets from 1997.
Besides the JRE is too big and fat to be successful in the long run and talks to do something about it date back to like 2005 and nothing serious has been done, and won't be done.

---

### Post by Unterseeboot_234 on 2012-12-18
Bird,

I don't like what Oracle is doing with Java. To register for beta tools gets a daily spam from them bout how to add an Oracle subscription service to my server. Obviously there will be changes. The FX runtime .jars for version 2.2 now include pathways that start with com.oracle.javafx.*. There was a JRE6 update where they tried that same name change and broke backwards compatiability.

I remember the original release of Swing as the JFC.jar. Lots of confusion until the jars got reconfigured into com.sun.javax.swing.*.

The trend I'm seeing is Windows8 is hardware specific now. So is JavaFX. FX might become a Win add-on and nothing more. Oracle is not as academic as Sun Microsystem was. It is my suspicion Java8 will be a break with legacy code. Oracle wants a JRE that accepts a variety of languages.

I wished there was a Ubuntu/Android answer. FX was a blind end trail for me and I think Oracle is running out of time to make a new standalone technology. I wrote pretty much the same thoughts to the FX developers and they insist a Ubuntu version is coming.

---

