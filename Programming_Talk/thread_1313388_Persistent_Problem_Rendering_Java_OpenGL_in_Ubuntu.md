---
title: "Persistent Problem Rendering Java OpenGL in Ubuntu"
date: 2009-11-03
forum: Programming Talk
---

### Post by kfsorensen on 2009-11-03
Hello,

I have a very aggravating problem with some Java code that I've written that uses the Java Open GL (JOGL) library files to create some nice graphical displays.

So far, I've encountered this problem on

1.  A Dell D600 Latitude laptop running Jaunty and later Karmic.
2.  An HP desktop running Jaunty and later Karmic.
3.  An HP Pavilion laptop running Karmic.

What really perplexes me is that other folks have gotten these programs to run just fine on their Ubuntu installs.  If no one could get it to work, that would be one thing.  But the fact that they work for some and not for others (like me) is incredibly frustrating.

Here's a good example of one of the programs that are using JOGL and Java Web Start as a distribution method:

[http://www.astrojava.com/lunar/](http://www.astrojava.com/lunar/)

It looks like this when I run it on any of those three machines:

---

### Post by ondrejch on 2009-11-04
I downloaded the LunarTrajectory.jnlp and this is how I got it working on Eeebuntu, somehow:

1) I switched to sun java6 by 
$ sudo update-java-alternatives -s java-6-sun

2) Tried to run as 
$ javaws Desktop/LunarTrajectory.jnlp 
- no luck - "Unable to load source ... ", when trying to download further code.

3) Tried to run it as root, assuming it wants to download something
$ sudo javaws Desktop/LunarTrajectory.jnlp 
and it works, with the rendered Earth and Moon, one can mouse-grab the scene etc.

Here is my java version:
$ java -version
java version "1.6.0_16"
Java(TM) SE Runtime Environment (build 1.6.0_16-b01)
Java HotSpot(TM) Server VM (build 14.2-b01, mixed mode)

---

