---
title: "Open-source JPEG reader/writer?"
date: 2007-12-23
forum: Programming Talk
---

### Post by Sporkman on 2007-12-23
I'm interested in messing around with image processing/editing routines, etc, but I don't want to go through the trouble of writing a JPEG reader/writer. 

Can anybody point me to an open-source c/c++ JPEG reader/writer? Something along the lines of a function that I can call, that'll return a simple 2D array of pixel info, then send it back (modified, perhaps) to be written to file...

---

### Post by Sporkman on 2007-12-23
Looks like this may be what I'm looking for:

[http://www.faqs.org/faqs/jpeg-faq/part2/section-15.html](http://www.faqs.org/faqs/jpeg-faq/part2/section-15.html)

---

### Post by slavik on 2007-12-23
this might be overkill, but SDL has an addon library called SDL_image which can read JPEGs (not sure how it writes them or if it can at all).

---

### Post by wolfbone on 2007-12-23
SDL_image uses IJG's libjpeg. AFAIK, most jpeg-using FOSS does. The OP found the right library for jpeg I/O (albeit using a strange search method!).

---

### Post by KCPokes on 2007-12-23
I was going to suggest ImageMagik, but not going to work with C++.  Instead you might look at CImg ([http://cimg.sourceforge.net/](http://cimg.sourceforge.net/)) which can actually use different image processing libraries.

---

### Post by TJRC on 2012-02-17
> **KCPokes said:**
> I was going to suggest ImageMagik, but not going to work with C++. 

There's Magick++, [http://www.imagemagick.org/Magick++/](http://www.imagemagick.org/Magick++/)

---

### Post by nothingspecial on 2012-02-17
[IMG]http://img845.imageshack.us/img845/6976/necro2.png[/IMG]

---

