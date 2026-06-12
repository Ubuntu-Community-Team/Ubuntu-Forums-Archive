---
title: "Advice with  Open gl , with java or cpp ?"
date: 2010-10-03
forum: Programming Talk
---

### Post by Shpongle on 2010-10-03
Hey all , Im planning on doing my final year project for college with open gl . I have a years programming experience in cpp and java so the language is not an issue in that sense. I would be developing an e learning tool that would based heavily on 3d animations of different sizes and complexities. Im thinking to do it in java because it would be cross platform and it would mean I wouldn't have to rely on the native libraries to deal with the window management as thats taken care of with swing and awt. 

While that sounds all good , I could really do with the brush up in cpp , so doing this would give me that boost since I'd be working on it all year. the problem now is that I would still like it to be cross platform , but that means using gtk+ (as far as I know windows supports it too). I have no experience with this , Im willing to learn but I need to hit the ground running on this one. Loads of coding involved for what Im planning.

just wondering on what yous think and your experiences with gtk+ (other gui libraries) and open gl in either . 

Thanks

---

### Post by WitchCraft on 2010-10-03
> **Shpongle said:**
> Hey all , Im planning on doing my final year project for college with open gl . I have a years programming experience in cpp and java so the language is not an issue in that sense. I would be developing an e learning tool that would based heavily on 3d animations of different sizes and complexities. Im thinking to do it in java because it would be cross platform and it would mean I wouldn't have to rely on the native libraries to deal with the window management as thats taken care of with swing and awt. 

While that sounds all good , I could really do with the brush up in cpp , so doing this would give me that boost since I'd be working on it all year. the problem now is that I would still like it to be cross platform , but that means using gtk+ (as far as I know windows supports it too). I have no experience with this , Im willing to learn but I need to hit the ground running on this one. Loads of coding involved for what Im planning.

just wondering on what yous think and your experiences with gtk+ (other gui libraries) and open gl in either . 

Thanks

When you know java and C++ already (one year hardly qualifies as knowing even one, much more two), then why not try C# with GTK# or wxWidgets?
You can still use OpenGL and have it cross plaform, as mono (.NET runtime) runs on Linux, and you can pinvoke native libraries.

---

### Post by Shpongle on 2010-10-03
> **WitchCraft said:**
> When you know java and C++ already (one year hardly qualifies as knowing even one, much more two), then why not try C# with GTK# or wxWidgets?

I never said I "know" them in that sense. What I meant was I know how to use them , control flow , oo approach and concepts , api's etc. Technically I have about 2 years in each but was only taught in both for 1, anyway  I will be doing more development in both during the year in other subjects. I really wont have time for c# and for what im planning I want to use open gl. What im looking for is opinions on the libraries ?

---

### Post by WitchCraft on 2010-10-05
> **Shpongle said:**
> I never said I "know" them in that sense. What I meant was I know how to use them , control flow , oo approach and concepts , api's etc. Technically I have about 2 years in each but was only taught in both for 1, anyway  I will be doing more development in both during the year in other subjects. I really wont have time for c# and for what im planning I want to use open gl. What im looking for is opinions on the libraries ?

My opinion is that SDL and OpenAL is the way to go, for 3D and cross-platform anyway, take Quake3/OpenArena as reference.
It certainly is a well-crafted framework, and the only working one of its kind.

If you use GTK, wxWidgets or QT is a matter of debate.
I have always favoured wxWidgets over the former two, because it uses native widgets on all platforms, that in contrast to the old-fashioned look of GTK/QT, which is a definitve disadvantage if you intend to sell just about any product. wxWidgets has its own share of problems though, just as the other two.

Lately I'm changing over to GTK, not because I think it's good, but because I use C#/VB.NEt at work, and when I want to port any app to Linux, there's only GTK#, apart from an alpha release of wxWidgets, of which I don't know for how long the project will continue/be maintained - which is kind of a definitive no to using it.

---

### Post by WitchCraft on 2010-10-05
> **Shpongle said:**
> I never said I "know" them in that sense. What I meant was I know how to use them , control flow , oo approach and concepts , api's etc. Technically I have about 2 years in each but was only taught in both for 1, anyway  I will be doing more development in both during the year in other subjects. I really wont have time for c# and for what im planning I want to use open gl. What im looking for is opinions on the libraries ?


**[COLOR="red"]Malfunction - Please delete this entry.[/COLOR]**

My opinion is that SDL and OpenAL is the way to go, for 3D and cross-platform anyway, take Quake3/OpenArena as reference.
It certainly is a well-crafted framework, and the only working one of its kind.

If you use GTK, wxWidgets or QT is a matter of debate.
I have always favoured wxWidgets over the former two, because it uses native widgets on all platforms, that in contrast to the old-fashioned look of GTK/QT, which is a definitve disadvantage if you intend to sell just about any product. wxWidgets has its own share of problems though, just as the other two.

Lately I'm changing over to GTK, not because I think it's good, but because I use C#/VB.NEt at work, and when I want to port any app to Linux, there's only GTK#, apart from an alpha release of wxWidgets, of which I don't know for how long the project will continue/be maintained - which is kind of a definitive no to using it.

---

### Post by jespdj on 2010-10-08
If you're going to use Java:

There are multiple OpenGL bindings for Java. The more or less "official" (it's on its way to become the standard, but is not yet) binding is [JOGL](https://jogl.dev.java.net/). Also [LWJGL](http://lwjgl.org/) (Lightweight Java Gaming Library) might be interesting, it has its own OpenGL binding.

One nice thing about using Java is that it is cross platform, you have to do (almost) nothing to make your software work on Linux, Windows, Mac OS X and other operating systems; you don't even have to recompile your software for different operating systems.

---

### Post by directhex on 2010-10-08
> **jespdj said:**
> If you're going to use Java:

There are multiple OpenGL bindings for Java. The more or less "official" (it's on its way to become the standard, but is not yet) binding is [JOGL](https://jogl.dev.java.net/). Also [LWJGL](http://lwjgl.org/) (Lightweight Java Gaming Library) might be interesting, it has its own OpenGL binding.

One nice thing about using Java is that it is cross platform, you have to do (almost) nothing to make your software work on Linux, Windows, Mac OS X and other operating systems; you don't even have to recompile your software for different operating systems.

What he said, with Tao, OpenTK, and Mono.

---

### Post by ziekfiguur on 2010-10-08
I personally rather dislike the java bindings for openGL, and if you use an option like SDL your program will work cross-platform too. 
Also, i found that java sometimes has bugs that occur only at certain operating systems so it may be rather hard to debug 
(This may be true for c++ too, but the c++ standard library is usually stable).
So, if you are not significantly better at java i would advice for c++, but that's just my two cents.

---

### Post by WitchCraft on 2010-10-08
Ultimately, it's a decision of execution speed vs. development speed.

I personally think Java is too slow/unresponsive/buggy while C++ makes you too slow in development.

Therefore I opt for C# + TAO Framework, which is nearly as fast as C++ (sometimes even faster, due to good GC engine), and far less unresponsive, and also it already has less bugs than Java.

The advantage of using C# is you can use pointers, pass by reference and pinvokes (native dll calls, on Linux too), which means you can always resort to native dlls or mixing with C++, which is something that is more complex with Java.

PS: mono 2.8 stable is out (C# 4.0)...

---

