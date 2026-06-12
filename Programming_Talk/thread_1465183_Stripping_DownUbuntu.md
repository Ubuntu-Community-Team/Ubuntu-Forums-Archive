---
title: "Stripping DownUbuntu"
date: 2010-04-29
forum: Programming Talk
---

### Post by talguy on 2010-04-29
I have create a program that replaces my car's instrument cluster by receiving data about the car via OBD-II and a microcontroller.  The program runs fine on my test computer but the intent is to have it run on a via/atom platform which is a significant performance decrease compared to the dev computer.  What and how would I stream line ubuntu so that it would run even more efficient than it already does for this real time application.

I am using gtkmm and cairo for my interface

---

### Post by tookyourtime on 2010-04-30
Don't bother stripping it down, just use a lightweight distribution.

[http://www.ubuntu.com/products/mobile](http://www.ubuntu.com/products/mobile)

[http://fluxbuntu.org/js.html](http://fluxbuntu.org/js.html)

---

### Post by mmix on 2010-04-30
gui -> cli(ncurses)
c++ -> c/asm
algorithms tune.

---

### Post by soltanis on 2010-05-01
Hope you bug test it if you're running it in your car.

Definitely use a stripped down custom Linux distribution. There's one that runs in like, 10 MB of RAM (Tiny Core Linux). Definitely replace glibc with ulibc and use busybox core tools vs gnu utilities. There's some guides on the Internet, I think, for basically "growing" your own Linux system from various distributions. This might be what you need given your specific hardware.

---

### Post by talguy on 2010-05-02
I've been doing a lot of debugging and tuning of the app so far it is running.  Fluxbuntu looks good but my question is does it support the gtkmm library?  I'm trying to stay with this library so that I don't have to reprogram the entire app.  I think I read some where that xfce supports the library, maybe I could use xbuntu and just uninstall what I don't need, i.e. networking, pointless apps, etc.

---

### Post by snowpine on 2010-05-02
Fluxbuntu is obsolete as of April 2009. :(

You want the Minimal Ubuntu CD I think: [https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)

libgtkmm is in the repositories for all currently-supported Ubuntu releases.

---

### Post by talguy on 2010-05-02
> **snowpine said:**
> Fluxbuntu is obsolete as of April 2009. :(

You want the Minimal Ubuntu CD I think: [https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)

libgtkmm is in the repositories for all currently-supported Ubuntu releases.

Thanks Snowpine, that is exactly what I am looking for

---

### Post by talguy on 2010-05-03
What would be a good light weight window manager I should install that supports gtkmm?

---

