---
title: "Capture what need to be draw from app"
date: 2012-02-13
forum: Programming Talk
---

### Post by ripi0 on 2012-02-13
Hello guys, I'm absolutely newbie in programming with ubuntu specifics API (specially cause I don't know where to find them).

But I'm trying to do a task, that I think is possible. I wanna to grab the painted image of some program (saved as an image Object, or just an an (A)RGB matrix). But the difficult part, is that I want to do that, with the software window, even if that is partially covered by another window.

So I don't wanna to just take an screenshot from video and cut the part of image corresponding to the app window that I want to grab. I want to grab how the application "should be drawn" considering there is not over it.

How can I do that in C/C++ programming in Ubuntu ?
**Even if you have no idea of how to do that, can you point me to some API documentation related to that?**

Thanks in advance.

---

### Post by ofnuts on 2012-02-13
> **ripi0 said:**
> Hello guys, I'm absolutely newbie in programming with ubuntu specifics API (specially cause I don't know where to find them).

But I'm trying to do a task, that I think is possible. I wanna to grab the painted image of some program (saved as an image Object, or just an an (A)RGB matrix). But the difficult part, is that I want to do that, with the software window, even if that is partially covered by another window.

So I don't wanna to just take an screenshot from video and cut the part of image corresponding to the app window that I want to grab. I want to grab how the application "should be drawn" considering there is not over it.

How can I do that in C/C++ programming in Ubuntu ?
**Even if you have no idea of how to do that, can you point me to some API documentation related to that?**

Thanks in advance.ksnapshot (part of KDE) can do that, so have a look at the source code?

---

### Post by ripi0 on 2012-02-13
I give a look at the source code, but they use Qt to grab window screen. I was looking for something more low level, that let me get the image of some software window that isn't necessary 100% displayable on the screen.

I found some method on Xlib, the [XGetImage(...)]("http://tronche.com/gui/x/xlib/graphics/XGetImage.html"), but seems that this lib is used with linux-windows server communication, so I don't know if i can use that in an simple desktop application.

---

### Post by MG&amp;TL on 2012-02-13
> **ripi0 said:**
> 

I found some method on Xlib, the [XGetImage(...)]("http://tronche.com/gui/x/xlib/graphics/XGetImage.html"), but seems that this lib is used with linux-windows server communication, so I don't know if i can use that in an simple desktop application.

Of course you can. Pretty much any graphical application on Linux today uses X.org (and by extension Xlib). I think you're getting confused as to what X does, see the [X.org page]("http://www.x.org/wiki/") for more details on X's function.

---

