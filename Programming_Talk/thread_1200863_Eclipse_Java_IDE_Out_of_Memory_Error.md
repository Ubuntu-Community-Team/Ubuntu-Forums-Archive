---
title: "Eclipse Java IDE: Out of Memory Error"
date: 2009-06-30
forum: Programming Talk
---

### Post by SNYP40A1 on 2009-06-30
I found this post helpful ([http://forums.whirlpool.net.au/forum-replies-archive.cfm/1104846.html):](http://forums.whirlpool.net.au/forum-replies-archive.cfm/1104846.html):)

> 
Haha thanks for the help everyone, that worked wonders!
(Window -> Preferences -> Java, Installed JRE's -> Double clicking on the JRE, under VM Arguments adding -Xmx1024m)

Eeek, are you sure you want to do THAT?

Keep in mind that now every Java program you use can use up 1Gb of memory... and keep in mind that JVM instances

a) don't share memory
b) do not release memory until the JVM exits

So... don't make max memory 1Gb by default. You really should be allocating that parameter for that particular program only

It's important to note that you can't increase the memory size by adding the adding the -Xmx1024m argument in the Argument box under run configuration in Eclipse!  Took me too long to figure that out.

---

