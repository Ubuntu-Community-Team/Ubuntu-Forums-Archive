---
title: "C++ and Java and Games"
date: 2014-07-12
forum: Programming Talk
---

### Post by Sir_Sword on 2014-07-12
When it comes to game programming, I don't think Java is the first language most people think of.  They usually think of C++ and other languages.  The biggest name in Java gaming is Minecraft, and there are a few other Java-based desktop games out there, but not nearly as many as there are C++.

When it comes to C++ vs. Java for game programming one obvious advantage of C++ is speed.  The resulting program should generally run faster.  But with Java being at least somewhat simpler to program in than C++, are there any other advantages C++ has over Java for game programming?

---

### Post by trent.josephsen on 2014-07-13
[Here's a recent /r/Minecraft thread you might find interesting](http://www.reddit.com/r/Minecraft/comments/2ag4zi/discussion_if_minecraft_was_to_be_developed_from/), but take TheRuiner_'s top level comment as a warning.

Notably, Java doesn't have to be slow. Minecraft's performance issues are almost universally the result of poor design decisions in Minecraft, not the fault of the Java language or runtime. (Notch originally wrote the game in his spare time, and it was never designed to be fast.) And like you said, there aren't many other Java-based games out there, so the sample size is small. (I don't know any others off the top of my head, but Terraria for instance uses C#.)

I am not a game programmer, I don't know C++, and I am therefore wholly unqualified to say what I am about to say. However, it seems to me that games are almost the sole holdout for C++ these days, in terms of new development. C++ is having its lunch eaten by higher level languages just about everywhere (except in the embedded space, where it never managed to dethrone C). But when it comes to games, C++ is "the worst possible language, except for all the others". C++ doesn't have quite the distribution issues of Java ("But I have Java 1.7! Why won't it work? Oh, I need *Oracle's* 1.7? Ok, I did that and now my keys stick sometimes..."), which is a mark in its favor (although some developers try to neutralize this advantage by using DirectX). Also I believe most existing game engines are written in C++.

Another option, probably a better one, is to use a higher level language (i.e., neither C++ nor Java) for game logic and UI, on top of an engine written in C++ (since pretty much all engines are). I understand Lua is popular for this purpose; personally I could never get over 1-based indexing. But there you have it: pretty much all I know about game programming beyond NetHack. I feel obligated to observe that you may get better quality responses on a forum dedicated to game development.

---

### Post by CptPicard on 2014-07-13
Game programming in Java nowadays means pretty much using some kind of OpenGL bindings, and at that point you've already offloaded a big part of performance-critical stuff onto the library code (and eventually hardware). For other performance bottlenecks, Java should be quite OK, and it's even high-level enough for you to comfortably write and test more abstract stuff such as game AI. However, I  am not sure how smooth Java's garbage collector is these days -- it's not nice having your game stutter every now and then because of a gc pass.

---

### Post by Sir_Sword on 2014-07-14
> **CptPicard said:**
> Game programming in Java nowadays means pretty much using some kind of OpenGL bindings, and at that point you've already offloaded a big part of performance-critical stuff onto the library code (and eventually hardware). For other performance bottlenecks, Java should be quite OK, and it's even high-level enough for you to comfortably write and test more abstract stuff such as game AI. However, I  am not sure how smooth Java's garbage collector is these days -- it's not nice having your game stutter every now and then because of a gc pass.

I do hear people complain quite a bit about Java's garbage collector, giving it as a reason why they think games shouldn't be made in Java.  I'm not sure how big a difference it really makes in performance these days, but I know that at least in Minecraft there's a half-second stutter every now and then which might be the garbage collector, or it might be the client loading in more data and blocks, I don't know.  I've also played Spiral Knights which is kind of a fun light online game that has a downloadable .jar client, and it's always been super smooth.

---

### Post by Sasha_Aderolop on 2014-07-17
Creating computer games with the computer experience you have is not nearly enough (Honest look at it). If you've never computer programmed before, tackling such a project with just tutorials...well your gonna be in a complete mess. Learning programming by tutorials or buying a giant manual is very inefficient, stressful, and time consuming. Your gonna be confused as heck, trust me. If you have interest in building games, I first suggest you take a couple of classes on programming languages such as C++, Java, Digital Design, etc. 

 If you really have the motivation to create games, its gonna be A LOT of work. There are a ton of things you have to learn. It could take years of practice before creating just a decent game. 

 Gotta say your over your head in this one. You can definitely pursue this path. Just don't expect to finish this project in just a couple of months.

---

### Post by Sir_Sword on 2014-07-17
> **Sasha_Aderolop said:**
> Creating computer games with the computer experience you have is not nearly enough (Honest look at it). If you've never computer programmed before, tackling such a project with just tutorials...well your gonna be in a complete mess. Learning programming by tutorials or buying a giant manual is very inefficient, stressful, and time consuming. Your gonna be confused as heck, trust me. If you have interest in building games, I first suggest you take a couple of classes on programming languages such as C++, Java, Digital Design, etc. 

 If you really have the motivation to create games, its gonna be A LOT of work. There are a ton of things you have to learn. It could take years of practice before creating just a decent game. 

 Gotta say your over your head in this one. You can definitely pursue this path. Just don't expect to finish this project in just a couple of months.

Thanks for the thought-out reply.

To give a little background on myself, I'm a professional software engineer specializing in Java and Python, though I've also done work in C and C++ when I've absolutely had to, to hook into some Microsoft stuff.

I've been in Java almost since it started, Python is a somewhat newer thing for me.  I've worked on both client applications and large Java EE projects.  I've just never made games before, besides dabbling in creating a few smaller Java game engines a number of years ago, and making a pile of text adventures both for modern systems and more recently, for the Commodore 64.  Because it's the Commodore 64.

I don't have any specific game project in mind right now.  I'm just gathering information about current capabilities and attitudes.

Coincidentally, I've always learned best from manuals and books :).

---

