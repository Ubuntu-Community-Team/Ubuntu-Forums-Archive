---
title: "what programing language do you recomend"
date: 2009-08-20
forum: Programming Talk
---

### Post by JUSTINBEAIRD on 2009-08-20
hello i would like to learn a computer programing language
i am quite good with php css html and briefly studied javascript, ajax and "oo php"
i am not quite sure which one i should start with
one of the c programing languages is where i would like to start but do not  know much about he differences 
c# c c++

---

### Post by Mirge on 2009-08-20
[http://ubuntuforums.org/showthread.php?t=1006666](http://ubuntuforums.org/showthread.php?t=1006666)

---

### Post by lisati on 2009-08-20
[http://ubuntuforums.org/showthread.php?t=1006662](http://ubuntuforums.org/showthread.php?t=1006662)

---

### Post by JUSTINBEAIRD on 2009-08-20
thank you those links are great help but maybe I should explain what I want to do and know

I would like to know how mp3's and other audio video files are decoded and know how to do it 

I would like to use python with them for linux which I read c was better with python 

I would like to to build portable aps for windows and not sure what gui to use for this or what libraries are available for it 

someday in the far future I would like to build a very simple gui on an old laptop to be a mp3 player or whatever I want for the fun of it


sorry if this is the same old newbe post but this is madning trying to figure out where to start

---

### Post by Copernicus1234 on 2009-08-20
If you want to write a codec, you will probably need to use C I think, at least if you want to write all the low detail stuff yourself and dont use any other peoples libraries for it. But its not really 
something you do on your first day of C. Its probably quite difficult.

---

### Post by JUSTINBEAIRD on 2009-08-20
> **Copernicus1234 said:**
> If you want to write a codec, you will probably need to use C I think, at least if you want to write all the low detail stuff yourself and dont use any other peoples libraries for it. But its not really 
something you do on your first day of C. Its probably quite difficult.

I know it's a long way off :) but am trying to look ahead

---

### Post by Copernicus1234 on 2009-08-20
Well, I would learn the basics of C and then start looking into a open source formats such as the ogg formats, learn how they store data and then write a program to play the file. After doing that, you can modify the format and the codec to whatever you want so it becomes your codec. :)

---

### Post by mess110 on 2009-08-20
depends on what you want. personally I like java.

---

### Post by kpkeerthi on 2009-08-20
[Learn Java]("http://www.amazon.com/Head-First-Java-Kathy-Sierra/dp/0596009208/ref=sr_1_7?ie=UTF8&s=books&qid=1250767203&sr=1-7")

---

### Post by CptPicard on 2009-08-20
Lossy audio format codecs for formats like mp3 are rather mathematically involved... they have nothing to do with C per se, but the actual problem is probably too hard for a beginner to handle.

---

### Post by Drone022 on 2009-08-20
> Lossy audio format codecs for formats like mp3 are rather mathematically involved...

Pretty sure you would have to read up on [forward/inverse discrete cosine transforms]("http://en.wikipedia.org/wiki/Discrete_cosine_transform"). I know they at least apply to mpeg and such.

---

### Post by pepperphd on 2009-08-20
> **Drone022 said:**
> Pretty sure you would have to read up on [forward/inverse discrete cosine transforms]("http://en.wikipedia.org/wiki/Discrete_cosine_transform"). I know they at least apply to mpeg and such.

[IMG]http://upload.wikimedia.org/math/9/9/d/99db2c8c49465a6e2b28163abcab5be3.png[/IMG]

No thanks man.

---

### Post by nvteighen on 2009-08-20
You're not even a beginner... Why restrict yourself to that specific goal? Ok, it's good to have goals to fulfill in this life, but in this specific stage, it should be IMO, just to learn how to program in general... It sounds more reasonable to me, at least. You never know, you always might find in your journey something new that interests you... AI, system programming, network, web development, Computer Science, etc.

Keep your mind open to new possibilities, always ;)

---

### Post by JUSTINBEAIRD on 2009-08-20
> **nvteighen said:**
> You're not even a beginner... Why restrict yourself to that specific goal? Ok, it's good to have goals to fulfill in this life, but in this specific stage, it should be IMO, just to learn how to program in general... It sounds more reasonable to me, at least. You never know, you always might find in your journey something new that interests you... AI, system programming, network, web development, Computer Science, etc.

Keep your mind open to new possibilities, always ;)

thank you for all your reply's im going with c
these weren't exactly short term goals but some of the things I want to understand some day and so much more 
I can dream :)

also I am quite fond of math i may not be able to spell or use correct grammer but i do love to study math :)

---

### Post by Can+~ on 2009-08-20
I'll summarize the whole following comments: Go with python. Easy, powerful, teaches you good manners (indentation), provides a solid base for later moving to lower-level languages or other paradigms.

As for your idea, I normally have some papers around with ideas to do when I have some free time and/or experience. Yours is one of those cases, write it for later development, when you're a mature programmer.

---

### Post by haemulon on 2009-08-20
> **JUSTINBEAIRD said:**
> 

also I am quite fond of math i may not be able to spell or use correct grammer but i do love to study math :)


As you know by now C and C++ are not recommended for the beginner programmer.

The good programmers like math though, so that's a good start.

---

### Post by soltanis on 2009-08-20
> **Copernicus1234 said:**
> Its probably quite difficult.

Understatement of the hour. Codecs are much more theoretical than they are programming implementation anyway.

---

### Post by gjosef on 2009-08-21
> **mess110 said:**
> depends on what you want. Personally i like java.

+1

---

### Post by bender1234 on 2009-08-23
> **JUSTINBEAIRD said:**
> hello i would like to learn a computer programing language
i am quite good with php css html and briefly studied javascript, ajax and "oo php"
i am not quite sure which one i should start with
one of the c programing languages is where i would like to start but do not  know much about he differences 
c# c c++

java/c# managed code ok for typical non intensive gui applications, databases etcetc. Nicer framework, and you don't have to worry about pointers and certain memory errors etc. Uses alot of resources, again particulary ram, and you don't really have control over it, the garbagecollecter lives it's own life.

c++/c good for intensive stuff where you use a lot of resources. Typically used for anything with graphics(games, video, rendring etc). In comparison to managed code, when you tell your program to free resources it does it. Needed for more low lvl stuff. Speed gimme what I need! :)

c still used for the most low lvl os stuff, like kernel and driver programming etc.

---

### Post by Reiger on 2009-08-23
Quite mathematically involved. Asymptotics... are hard.

Also: with a proper strategy w.r.t. buffering just about any language implementation (be it native code, or interpreted python) should be able to give you satisfactory (i.e.: smooth, no gaps) playback. Decoding is usually the non-intensive work of media handling anyways (because many formats must be capable of being played in pseudo real time even on mediocre systems).

---

