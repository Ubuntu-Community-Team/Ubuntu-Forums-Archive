---
title: "JavaFx"
date: 2008-11-29
forum: Programming Talk
---

### Post by accesshater on 2008-11-29
Hi there my fellow programmers :)

I have a question about javafx. The launch of the sdk wil be on 4-12-2008 ([http://www.javafx.com/](http://www.javafx.com/)). 
I guess the SDK wont be a problem... but will there be updates for the java runtime environment on that day... or will these updates be delayed on ubuntu?

Because if the JRE isnt updates you cant use java fx applications

---

### Post by Zugzwang on 2008-11-29
The new runtime environment/SDK *might* make it into the next release of Ubuntu, Jaunty. See the [schedule]("https://wiki.ubuntu.com/JauntyReleaseSchedule") for details. So if it's in Debian before the deadline, it might be in.

If you need the very-latest software in Ubuntu, you have to install it manually. This is mainly because the Ubuntu people need to make feature/import freezes in order to hunt the most inportant bugs before the release dates.

---

### Post by accesshater on 2008-11-29
> **Zugzwang said:**
> The new runtime environment/SDK *might* make it into the next release of Ubuntu, Jaunty. See the [schedule]("https://wiki.ubuntu.com/JauntyReleaseSchedule") for details. So if it's in Debian before the deadline, it might be in.

If you need the very-latest software in Ubuntu, you have to install it manually. This is mainly because the Ubuntu people need to make feature/import freezes in order to hunt the most inportant bugs before the release dates.

Hmm sounds logical :)

Tnx! Im already looking forward to Jaunty

---

### Post by jamesstansell on 2008-12-06
The javafx jar itself seems to run ok on java 5.  Some of the media stuff uses native libraries and linux is not supported yet, although sun says they are working hard on it.

The java 6u10 release was said to include some javafx-related stuff, but I'm not sure what exactly.  At any rate this release was included in ubuntu 8.10 (intrepid.)

Java 6u11 was released this week to address security issues, mostly.  I haven't heard of any javafx-related changes in it.  However it is already packaged for ubuntu.  I was able to grab the deb files from the 9.04 (jaunty) repositories and install them on my 8.04 (hardy) box and use the browser plugin successfully.

Because it was a security release it will likely also be added to the other repositories before too long.

---

### Post by jespdj on 2008-12-06
Have a look at [this thread](http://ubuntuforums.org/showthread.php?t=876367) (scroll down to the newer posts).

---

