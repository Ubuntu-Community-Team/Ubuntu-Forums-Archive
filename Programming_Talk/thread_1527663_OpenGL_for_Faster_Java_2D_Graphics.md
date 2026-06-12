---
title: "OpenGL for Faster Java 2D Graphics?"
date: 2010-07-09
forum: Programming Talk
---

### Post by SNYP40A1 on 2010-07-09
I am trying to improve the performance of a Java library called JFreeChart.  It uses Java2D for drawing charts.  Is there a better library to use for 2D performance in Java?  Something tied closer to the hardware?  I imagine the answer I will get to this question will be use a different language if you care about performance.  But I'll ask anyway just to see if there's something that can improve upon Java 2D rendering.

---

### Post by myrtle1908 on 2010-07-09
> **SNYP40A1 said:**
> I am trying to improve the performance of a Java library called JFreeChart.  It uses Java2D for drawing charts.  Is there a better library to use for 2D performance in Java?  Something tied closer to the hardware?  I imagine the answer I will get to this question will be use a different language if you care about performance.  But I'll ask anyway just to see if there's something that can improve upon Java 2D rendering.

ChartDirector is excellent but not free.  I use it at work.  Never had any performance issues but I also didn't care much about performance.

[http://www.advsofteng.com/](http://www.advsofteng.com/)

---

### Post by SNYP40A1 on 2010-07-09
I would like to extend JFreeChart since I am already using it and very happy with it...just want faster rendering performance.  Thanks for the tip though...

---

### Post by Some Penguin on 2010-07-09
[http://java.sun.com/products/java-media/2D/reference/faqs/index.html#Q_How_can_I_get_better_performan]("http://java.sun.com/products/java-media/2D/reference/faqs/index.html#Q_How_can_I_get_better_performan")


[http://today.java.net/pub/a/today/2004/11/12/graphics2d.html]("http://today.java.net/pub/a/today/2004/11/12/graphics2d.html")

---

### Post by kahumba on 2010-07-10
A little off-topic.
When the OpenGL effort started the Linux OpenGL drivers where even worse than now and Sun never really invested enough effort into the OpenGL backend but rather used the noble excuse that the drivers (on Linux/Solaris) are bad hence no need to focus on an OpenGL backend too much.
Fast forward, the new JDK7 will ship with (x)Render acceleration, it's already approved and committed to the main dev tree but disabled by default for now, so we have to ask ourselves: what happens to the OpenGL pipeline, will it just be dropped or improved over time to match the snappiness of the window$ DirectX pipeline.

---

### Post by SNYP40A1 on 2010-07-10
> **Some Penguin said:**
> [http://java.sun.com/products/java-media/2D/reference/faqs/index.html#Q_How_can_I_get_better_performan]("http://java.sun.com/products/java-media/2D/reference/faqs/index.html#Q_How_can_I_get_better_performan")


[http://today.java.net/pub/a/today/2004/11/12/graphics2d.html]("http://today.java.net/pub/a/today/2004/11/12/graphics2d.html")

Thanks for the links Penguin.  I can see that the operations that I am using, mostly fillRect are already backed by OpenGL.  So part of my poor performance may be due to my integrated graphics solution, although I doubt it, only drawing about 1000 rectangles.  I'll look more into this tomorrow.

---

### Post by SNYP40A1 on 2010-07-10
> **kahumba said:**
> A little off-topic.
When the OpenGL effort started the Linux OpenGL drivers where even worse than now and Sun never really invested enough effort into the OpenGL backend but rather used the noble excuse that the drivers (on Linux/Solaris) are bad hence no need to focus on an OpenGL backend too much.
Fast forward, the new JDK7 will ship with (x)Render acceleration, it's already approved and committed to the main dev tree but disabled by default for now, so we have to ask ourselves: what happens to the OpenGL pipeline, will it just be dropped or improved over time to match the snappiness of the window$ DirectX pipeline.

Interesting note about JDK7.  Its release has been taking a long time.  I was expecting it back in 2008.  

I have to give M$ credit for DirectX, it appears to be a very powerful direct GPU / GPGPU language.  It's been around for 16 years now.  Not many individual actively-developed products last that long.  Linux just does not seem to have the driver support that Windows enjoys.  Although with Mac gaining popularity, hopefully the driver support will also benefit Linux users.

---

### Post by Some Penguin on 2010-07-10
> **SNYP40A1 said:**
> Thanks for the links Penguin.  I can see that the operations that I am using, mostly fillRect are already backed by OpenGL.  So part of my poor performance may be due to my integrated graphics solution, although I doubt it, only drawing about 1000 rectangles.  I'll look more into this tomorrow.

If you're uncertain about where performance bottlenecks lie, you should probably look into a profiler.  [http://www.yourkit.com/]("http://www.yourkit.com/") makes a nice one; it's not free, but there's a 15-day demo you can try.

---

### Post by kahumba on 2010-07-10
> **SNYP40A1 said:**
> Interesting note about JDK7.  Its release has been taking a long time.  I was expecting it back in 2008.  

I have to give M$ credit for DirectX, it appears to be a very powerful direct GPU / GPGPU language.  It's been around for 16 years now.  Not many individual actively-developed products last that long.  Linux just does not seem to have the driver support that Windows enjoys.  Although with Mac gaining popularity, hopefully the driver support will also benefit Linux users.
Roughly saying, OpenGL 3.3 = DirectX 10 & OpenGL 4.0 = DirectX 11 and neither of them is much faster than the other and neither has a "better" API, it's a matter of taste. The issue with Java's OpenGL pipeline is because it's not optimized because of the quality of the drivers and small desktop market share of Unix-like OSes hence Sun had a noble excuse to not bother seriously optimizing it.
Yes, JDK7 is taking pretty long to land, but mainly because there was the "Java 6 update 10" upgrade, plus Sun has been diverted by JavaFX.
JDK7 is scheduled for the Fall this year.

---

### Post by efikkan on 2010-07-10
Wich library do you intend to use for OpenGL? Lwjgl or jogl? 

In my experience Graphics2D will do if you are drawing not too complicated charts, maybe consisting of up to several hundred line segments. But if you are intending to create advanced charts to be interacted with, without lagging you might want to consider OpenGL.

The problem I find with OpenGL libraries for Java is linking the libraries in a runnable jar package. Some time ago when I was working on a school project my team decided to use lwjgl instead of Graphics2D because the "game" was not playable otherwise. We ended up launching the game through Java Web Start to make it run outside Eclipse. This silly project is the only time I've used OpenGL in Java, but I've been using it in C/C++ for many years. The link is in my signature.

So bottom line is, you will have to consider if the performance of the chart is too bad and if so try some OpenGL libraries, they will give you better performance. But if the performance is fine, I don't see any reason to use OpenGL, I don't think it's worth the effort.

-----

Regarding OpenGL and DirectX:

OpenGL is the competitor to Direct3D not DirectX.

OpenGL 3.2 is better featured than Direct3D 10, and has to be placed between Direct3D 10 and 11. OpenGL 2.x and 3.x include extensions for hardware tessellation for SM4 hardware, not as powerful as the SM5 tessellation, but more than powerful enough for most uses (powerful enough for any game I've seen). In addition OpenGL got faster draw calls, very good interaction between OpenGL and OpenCL, OpenCL is more powerful than DirectCompute, and is of course cross platform. As of today is the performance of OpenGL on nVidia hardware equal to Direct3D performance, but on AMD/ATI hardware OpenGL performance is bad. I work with these on a daily basis.

---

