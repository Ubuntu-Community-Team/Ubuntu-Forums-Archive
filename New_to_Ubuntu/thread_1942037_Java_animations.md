---
title: "Java animations"
date: 2012-03-16
forum: New to Ubuntu
---

### Post by Kenkoy on 2012-03-16
This problem concerns open JDK Java 6, when viewing weather satellite animations at [http://www.ghcc.msfc.nasa.gov/GOES/](http://www.ghcc.msfc.nasa.gov/GOES/)
I have Ubuntu 11.10, 64-bit, and Firefox 10.0.2. My machine: i5-2500K with 8 gigs RAM. Animations render with half the lower part of the image cut off, and some of the right side, as well. Results are the same no matter what settings I choose on the web page.
I just wonder if anyone else sees the same problem. If not, I'll assume it's a problem with my system. Thanks!

---

### Post by sammiev on 2012-03-16
> **Kenkoy said:**
> This problem concerns open JDK Java 6, when viewing weather satellite animations at [http://www.ghcc.msfc.nasa.gov/GOES/](http://www.ghcc.msfc.nasa.gov/GOES/)
I have Ubuntu 11.10, 64-bit, and Firefox 10.0.2. My machine: i5-2500K with 8 gigs RAM. Animations render with half the lower part of the image cut off, and some of the right side, as well. Results are the same no matter what settings I choose on the web page.
I just wonder if anyone else sees the same problem. If not, I'll assume it's a problem with my system. Thanks!

Try [Oracle (Sun Java)]("http://sites.google.com/site/easylinuxtipsproject/java") as I had to do the same years back.

---

### Post by Kenkoy on 2012-03-16
> **sammiev said:**
> Try [Oracle (Sun Java)]("http://sites.google.com/site/easylinuxtipsproject/java") as I had to do the same years back.

Thanks, sammiev, but Sun Java has increasing problems with security, according to what I've read in numerous places. I'm too new in Linux to take chances. I see, though, that if this problem hasn't been fixed in a few years, there's no use in me trying to solve it now.
Thanks again for your response!

---

### Post by QIII on 2012-03-17
Sun Java has also released frequent updates of late.  It is becoming more secure.

What you may be thinking is insecure is JavaScript, which is not Java.  The name causes some confusion -- the history of the name is probably too long to go in to here.  There are some very serious dangers associated with JavaScript, which is why many people run NoScript in their browsers. 

Although OpenJDK is supposed to be the reference implementation for Java 7 at some point, that may not be the case yet.  In any case, much of the world simply does not see OpenJDK as "Java".  Thus, many things you find on the web will not work - or will work poorly.  (That is what sammiev means by having to change some years back.  Some years back the compatibility of OpenJDK was even worse.  He does not mean that he had problems with Java some years back.)

Hopefully, the lack of recognition of OpenJDK in the world at large will change soon.  But that just isn't the case at the moment.

If you are concerned about security, do this:

Install Java as Sammiev suggests.  The instructions he pointed you to will activate the Java browser plugin.   If your content works, you know that the issue is Sun vs OpenJDK.  (By the way, if you were using Windows, you probably installed Java with a click when you went to a site with Java content.)

You may even want to try Java 7.

At that point, you can decide whether or not you want to use it or change your Java alternative back to OpenJDK.

---

### Post by Kenkoy on 2012-03-18
Yeah, I'm aware of JavaScript. That's not the issue in trying to render weather satellite animations, though. I'll take your advice re Java 7. There are still recent articles, tho, describing security problems with Sun JDK.
My issue is almost certainly Sun vs OpenJDK because my old computer developed the same problem when I recently upgraded its Lubuntu from an old version (From 9.10, I think).
Thanks again. I'm probably being too cautious because I'm new (at Linux, not computers).

---

