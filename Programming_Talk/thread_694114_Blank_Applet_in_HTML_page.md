---
title: "Blank Applet in HTML page"
date: 2008-02-11
forum: Programming Talk
---

### Post by Ultros88 on 2008-02-11
I am learning java and trying to test an applet I developed. The .java file compiles fine but when I open the html file containing the code:

<applet code="StaticRects.class" width=300 height=160></applet>

All I get is a black applet window.

I read online about a problem in fire fox that requires jdk-6u4 in order to be rectified so I dowloaded that .bin file.

Now I'm not really sure what to do with the extracted files to fix my initial problem of "why on Earth won't the applet run?".

Help is much appreciated,
Ultros

---

### Post by lnostdal on 2008-02-11
does applets work in general? try [http://java.sun.com/applets/jdk/1.4/index.html](http://java.sun.com/applets/jdk/1.4/index.html)

if not, try *sudo aptitude install sun-java6-plugin* then try the site again (restart firefox first, make sure you close down all firefox windows .. *ps -AF|grep firebox* should return nothing)

---

### Post by Ultros88 on 2008-02-11
Thanks a lot, it's working now.

Why wasn't it before? I assume that the plugin wasn't up to snuff for applets compiled in java-6. Is this right or is there some other reason?

I had noticed before I implemented your solution, that while other people's applets on webpages loaded, those on my own local file system would not. What was happening?

Thanks again!
Ultros

---

