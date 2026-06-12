---
title: "Java Problem (Visuals)"
date: 2005-10-28
forum: Programming Talk
---

### Post by Revert on 2005-10-28
I've gone through the steps to install 1.5 JDK and have confirmed that it was installed successfully and is set as my default Java provider.  However, I've been having a pretty weird problem...

I can compile and run everything but graphics.  I can get JLabels and the like to show up if I put them directly on a frame, but panels seem to mess it up.  The frame pops up and nothing else happens.  Before I installed 1.5 it had been working (I had the Blackdown 1.4 version), but now even when I go back and set that one as the default, it won't work.  
(Note: There is no fault in my code.)

I've used a variety of IDEs in testing this (NetBeans, jEdit, a few others), so I'm sure that's not the problem, it's something with the installation or something I'm not configuring (I'm new to Java, so I'm assuming it's the latter).  I talked to my Computer Science teacher and he said he had a similar problem one time on a Windows machine.  Apparently there was some second thing he downloaded to get it to work right.
Using 5.10, too.

I'm considering just reinstalling Ubuntu and trying it fresh.  Since this was only my second Linux distro, it's possible that I screwed it up while trying to accomplish some other task, and eliminating this possibility would help.

Right now I'm pretty clueless.  Has anyone else had the same problem?  Any ideas on how to fix it?

Thank you for your time.

---

### Post by jvictor on 2005-11-07
Make sure that u have Suns Java as ur java executable , the default** java** in Ubuntu points to gcj, u will have probs with that. also make sure ur are exporting you JAVA_HOME & PATH in ~/.bashrc. Make sure taht ur path has sun java in first precedence

---

