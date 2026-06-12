---
title: "OpenGL (C#) programming on Ubuntu?"
date: 2011-09-15
forum: Programming Talk
---

### Post by KreshDev on 2011-09-15
Greetings everyone,

I am still learning the C-Sharp language and I have made some console application games and I am now feeling like passing on to something a little bit harder. I would like to learn OpenGL programming, in the C# language. I have tried getting the libraries on Windows, but couldn't find any post or tutorial that wasn't outdated from 3 to 16 years, so I decided to search for those on Ubuntu and I have quickly found what I was looking for. I have already downloaded the libraries using the terminal:
```
sudo apt-get install freeglut3-dev
sudo apt-get install freeglut3
``` (or something around these lines)

However, I cannot find any good OpenGL C-Sharp tutorials and I don't know how to include the OpenGL headers. I have tried ```
using GtkGL;
``` , but it isn't working. Thanks in advance and sorry for my newbie question.

Please feel free to send me a PM, an e-mail (htcormier@googlemail.com) or even add me on Skype (tristan.cormier)!

---

### Post by true_friend on 2011-09-16
[SharpGL]("http://www.codeproject.com/KB/openGL/sharpgl.aspx")

---

### Post by KreshDev on 2011-09-16
Thank you for the tip, true_friend. I will try it out and see how it works for me.
Does anyone know of some good tutorials though?

---

### Post by Senesence on 2011-09-16
> **KreshDev said:**
> Thank you for the tip, true_friend. I will try it out and see how it works for me.
Does anyone know of some good tutorials though?

Not specifically for C#. 

Actually, even for C/++, there are few modern tutorials; most are still using deprecated calls like glVertex and such.

That said: Even if the syntax is slightly different, OpenGL is still OpenGL - the API should be essentially the same, even in C#, so C/++ tutorials are still fairly useful.

In the same respect, the "OpenGL Programming Guide" (aka: "The Red Book") is something you should probably look at.

Also, here are the few modern OpenGL articles/tutorials that I could find on the net, so have a look at that too:
[LIST=1]
[*][http://www.arcsynthesis.org/gltut/index.html](http://www.arcsynthesis.org/gltut/index.html)
[*][http://duriansoftware.com/joe/An-intro-to-modern-OpenGL.-Table-of-Contents.html](http://duriansoftware.com/joe/An-intro-to-modern-OpenGL.-Table-of-Contents.html)
[/LIST]

PS: Do you have to use C#? Why not C?

---

### Post by KreshDev on 2011-09-16
Thank you for the links, Senesence.
I would prefer to do it in C# as it is the language I know the most, but I might learn Java instead, because it kinda does the same thing. What would you suggest me? Java or OpenGL for a simple multi-platform 3D game?

---

### Post by Senesence on 2011-09-16
> **KreshDev said:**
> Thank you for the links, Senesence.
I would prefer to do it in C# as it is the language I know the most, but I might learn Java instead, because it kinda does the same thing. What would you suggest me? Java or OpenGL for a simple multi-platform 3D game?

Well, you can't compare Java to OpenGL in that way: Java is a language, OpenGL is a 3D graphics library.

Really, if you're programming on Linux, C# doesn't seem like the right choice (it's more in the context of Microsoft .NET, and so, you'll be hard pressed to find a whole lot of Linux specific, OpenGL-relevant information).

Even with Java, you'll need to use a wrapper library (probably around OpenGL) to communicate with the GPU, and while the Java interface structure may seem appealing at first, it actually turns out to be far more complicated than a C interface, because the people who write Java 3D engines tend to have their own "high-level" ideas about how 3D should work, which usually includes a very convoluted object hierarchy that you have to learn in addition to OpenGL.

Learn C. It's hard at first, but when you truly learn it, everything else is easier.

Here's a really good set of video tutorials (Stanford Lectures) that you can use: [http://www.academicearth.org/courses/programming-paradigms](http://www.academicearth.org/courses/programming-paradigms)

Jerry Cain is an awesome instructor!

---

