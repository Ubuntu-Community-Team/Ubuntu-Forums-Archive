---
title: "I'm not a programmer - could somebody please make this simple program for me?"
date: 2008-05-09
forum: Programming Talk
---

### Post by gottabeandrew on 2008-05-09
I have a logitech quickcam sphere MP. It works with aMSN, skype, luvcview and Cheese but doesn't work with Easycam, Camorama or flash. I don't know what the problem is with easycam and camorama but with flash, the only video feed option is one that doesn't work.

So, i want to know if somebody could please make a simple program that does one of these 2 things:

1. Displays my webcam image (can be as simple as luvcview) and then makes the live feed from my webcam into a video feed.
2. A plugin for luvcview or cheese which turns the output of those programs into a video feed.

This wouldn't just be beneficial to me, it would be beneficial to lots of other people with similar webcam problems.

Thanks.

---

### Post by dempl_dempl on 2008-05-09
Nope. People get payed for those things.

If you want to hire a programmer,

try

[http://www.getafreelancer.com/](http://www.getafreelancer.com/)

That kind of service costs  about 100-200$ on that site.

Cheers!

---

### Post by Wybiral on 2008-05-09
Or, you can learn a simple language (like Python or something) and write it yourself :)

---

### Post by dempl_dempl on 2008-05-09
> **Wybiral said:**
> Or, you can learn a simple language (like Python or something) and write it yourself :)

I believe he just wants to play with his camera :D   .

---

### Post by Wybiral on 2008-05-09
> **dempl_dempl said:**
> I believe he just wants to play with his camera :D   .

I believe (s)he wants a program.

---

### Post by dempl_dempl on 2008-05-09
> **Wybiral said:**
> I believe (s)he wants a program.

Perhaps . 

Anyway, if that's the case , this is a good site to start to program: 

[http://laroza.pbwiki.com/](http://laroza.pbwiki.com/)


Cheers!

---

### Post by Quikee on 2008-05-09
> **gottabeandrew said:**
> 
1. Displays my webcam image (can be as simple as luvcview) and then makes the live feed from my webcam into a video feed.

I don't know exactly what you mean by that it makes a "live feed" into a "video feed" but you can record the webcam output easily with gstreamer and a "simple" script.

```
#!/bin/sh

gst-launch-0.10 gconfvideosrc ! \
    video/x-raw-rgb,width=640,height=480 ! \
    ffmpegcolorspace ! \
    video/x-raw-yuv ! queue ! \
    tee name="tee" ! queue ! xvimagesink \
    tee. ! queue ! theoraenc quality=10 ! oggmux ! filesink location="test.ogg"
```

This script shows the webcam output (configured with "gstreamer-properties" aka "multimedia systems selector") in a window (size 640x480) and at the same time it records the output as a theora video (with quality 10) into a file with a name "test.ogg". 

If you read up a little on gstreamer you can make quite powerful things fairly simple.

---

### Post by gottabeandrew on 2008-05-09
If you want to do things with your webcam using flash (such as going on stickam.com where you display your webcam live) or on youtube where you can record directly from webcam using flash, it chooses a video feed/output but the one it chooses doesn't do anything and there isn't any other option. I want a program that creates an option, just like webcammax and manycam do for windows (maybe camorama or easycam do that too but i've never been able to use those two so i dunno). Manycam and webcammax don't work neither on ubuntu cause i've tried those using wine.

---

### Post by loell on 2008-05-09
an existing solution, but hard to set up for new users

[http://www.swift-tools.net/Flashcam/]("http://www.swift-tools.net/Flashcam/")

---

### Post by gottabeandrew on 2008-05-10
> **loell said:**
> an existing solution, but hard to set up for new users

[http://www.swift-tools.net/Flashcam/]("http://www.swift-tools.net/Flashcam/")

Could you possibly make me some simple instructions out of that please? I'd be most appreciative.

---

### Post by no2498 on 2009-09-05
to use flash
on the web you need to right click on the flash window
click allow
if you use it alot you can click remember

---

### Post by Tony Flury on 2009-09-06
On a completely different note - it always amuses me that people who aren't programmers describe programs that they want someone else to write as "simple". Lets be honest, unless you have a clue how to write the program in the first place - how can you have any idea that it is simple or not.

A program that is simple to describe (i.e. convert the output from my web cam into a videostream) is not neccessarily simple to write.

I am sure many of the programmers in this forum could describe an application which is dead easy to describe completely, but is in actual fact very complex to write.

---

### Post by nvteighen on 2009-09-06
> **Tony Flury said:**
> 
I am sure many of the programmers in this forum could describe an application which is dead easy to describe completely, but is in actual fact very complex to write.

Example: A text editor which folds and drag-drops code according to indentation level and readjusts it.

---

