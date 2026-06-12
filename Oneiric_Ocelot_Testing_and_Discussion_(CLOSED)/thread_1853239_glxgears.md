---
title: "glxgears"
date: 2011-10-01
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by Neo40 on 2011-10-01
I was boring today, so this morning I installed Wheezy Debian (testing) with xfce4. 
When I ran glxgears, I got around 20000 fps.
Then, I installed xubuntu 11.10 beta 2 and I was surprised when I see I get only 7200fps!
My video card is a nvidia gts 250.
Anyone knows why the results are different?

---

### Post by QIII on 2011-10-02
glxgears is not a benchmark and shouldn't be used as one.

You might try something like Gtkperf for a more valid test, but I don't know how heavily it taxes the gpu, if at all.

---

### Post by haresear on 2011-10-02
Perhaps due to different video drivers? Did you install any proprietary drivers? Xubuntu vanilla install will probably be using nouveau driver, not sure about Debian. Try running glxinfo and compare the outputs.

---

### Post by lucazade on 2011-10-02
> **QIII said:**
> glxgears is not a benchmark and shouldn't be used as one.

You might try something like Gtkperf for a more valid test, but I don't know how heavily it taxes the gpu, if at all.

gtkperf is only for 2d and gtk rendering.. it relies only on CPU.

while glxgears is not a real benchmark tool, it provides anyway 3d perfomance infos, even if basic.
obviously there are better suites to stress test gfx cards but I don't think this is the point.

> glxgears is an OpenGL program that reports FPS (frames per second) numbers. However, it is a very limited 'test'. Unlike most modern 3D games, glxgears:

- has an extremely low vertex/polygon count
- does no texturing at all
- only simple, flat shading is used (except inside the hole in each gear is simple smooth shading)
- all vertex data is stored in a display list, so almost nothing passes between host CPU and video card once rendering is started. This mostly implies video card fill rate is limited. But, see next point.
- the default window size is 300x300, a large part of which is not even rendered into, so it's not even a good fill rate test
- the entire render step consists of only 21 OpenGL functions calls, of which only 6 are unique. This is not a very good OpenGL API stress test. Something like glean would be better.

So to summarize, glxgears only tests a small part of what you typically see in a 3D game. You could have glxgears FPS performance increase, but your 3D game performance decrease. Likewise, you could have glxgears performance decrease and your 3D game performance increase. 

[http://wiki.cchtml.com/index.php/Glxgears_is_not_a_Benchmark](http://wiki.cchtml.com/index.php/Glxgears_is_not_a_Benchmark)

---

### Post by tista on 2011-10-02
Guys,

I could recommend Phoronix Test Suite...
That's more accurate. ;)

cheers.

---

### Post by Neo40 on 2011-10-02
> **haresear said:**
> Perhaps due to different video drivers? Did you install any proprietary drivers? Xubuntu vanilla install will probably be using nouveau driver, not sure about Debian. Try running glxinfo and compare the outputs.

Yes, I have installed proprietary driver (version 280.13) with xubuntu.
With Debian, it was also proprietary driver (I think it was version 275.?).

---

### Post by haresear on 2011-10-02
What desktop were you running with 11.10? 

When I experimented with Ubuntu 11.10 beta2 on an old Nvidia FX5200 card, I found that Unity 2D ran glxgears 3-4 times slower than Gnome-fallback. (Unity 3D and Gnome-shell would not run on that video card.)

---

