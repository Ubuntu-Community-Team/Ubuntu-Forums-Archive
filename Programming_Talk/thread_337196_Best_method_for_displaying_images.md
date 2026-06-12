---
title: "Best method for displaying images?"
date: 2007-01-12
forum: Programming Talk
---

### Post by Flubs4u on 2007-01-12
I want to develope an application that requires displaying multiple images from a file.  My previous application development experience is with C++, but I understand that rendering images is fairly difficult in C++.  I'm open to any suggestions of methods or different languages, but the end product has to be able to be cross platform.

Any and all help is appreciated!

---

### Post by Wybiral on 2007-01-12
> I understand that rendering images is fairly difficult in C++

Not if you use a library like SDL... SDL can load BMP's as-is, and with SDL_image, you can load all kinds of images.

What kind of app are the images being used in?
2d graphics...
3d graphics...
GUI?

---

### Post by Houman on 2007-01-12
Hi there,

There are many different image formats and dealing with each one of them is a pain. Thats why its best to use a library to do that. If youre developing GUIs with the gtk framework then gtk must have some utilities for loading some image format. 

I know for sure that wxwidgets supports a ton of image formats using the wxBitmap class, you can read more about it [here]("http://www.wxwidgets.org/manuals/2.6.3/wx_wxbitmap.html") . There are many more options out there, the gtk framework and QT and the rest will each have their own utility. 

Another option if you dont want to use their image libraries is to use many of the available image processing libraries that do not belong to any GUI framework (like gtk, QT...). One of the most famous ones is Magick++, its the C++ bindings for the ImageMagick developement libraries. You can read more about that [here]("http://www.imagemagick.org/Magick++/Documentation.html").

regards

Houman

---

### Post by Flubs4u on 2007-01-12
I've never worked with GTK before, and my knowledge of it is very limited, but I think something like that is right up my alley.  I'm putting together a picture viewer for viewing images in a series, so I will have to be doing GUI programming.  I want the end product to be platform independant and I know I've used GTK applications on windows and linux before, but does it work with mac OS too?  Also since I've never developed in GTK can anyone recommend an IDE or starting point to learn more?

---

### Post by Houman on 2007-01-12
hi there

If crossplatform-ability is your goal you should probably go with wxwidgets. QT and Java are also possible options (I prefer wxwidgets though). 

The thing with gtk is that although it is theoretically cross platform, the port to windows is apparently not as good as it ought to be. So i suggest that you go with one of the other options (Java, wxwidgets, QT). I think Java would probbaly be the easiest router to go.

As for Mac, I know for sure that wxwidgets is supported.

here is a link to get you started with wxwidgets : [http://en.wikipedia.org/wiki/Wxwidgets](http://en.wikipedia.org/wiki/Wxwidgets)

regards

---

### Post by Flubs4u on 2007-01-12
Any suggestions on a java IDE?

---

### Post by Houman on 2007-01-12
The most famous one is Eclipse: [http://en.wikipedia.org/wiki/Eclipse_IDE](http://en.wikipedia.org/wiki/Eclipse_IDE)

It is available on ubuntu and its a pretty good IDE.

Also I should mention you dont always need an IDE, at a minimum you need a compiler and a text editor. I myself code with emacs only and a lot of other developers dont depend on IDEs. Not that there is anything wrong with them, Im just saying you dont have to have them. But if you can get a hold of a good IDE like Eclipse, why not :D


Here is some instructions on installing and using Eclipse: [https://help.ubuntu.com/community/EclipseIDE](https://help.ubuntu.com/community/EclipseIDE)

regards

Houman

---

### Post by Grey on 2007-01-12
You know, I'm sorry.  I know there's a lot of Python evangelism around here.  But I am going to perpetuate that just a little more.  And it's because it really is a good language.  I've used many cross-platform applications.  Java and Python are two fairly common choices.

Eclipse: Written in Java.  Hogs memory like you wouldn't believe.

Azureus: Written in Java.  Very well featured, but hogs memory.  I use it because it has a couple of features I can't get anywhere else.

Bittornado: Written in Python.  Fast, and doesn't hog a lot of memory.

Picard Tagger: Written in Python with WxWidgets.  Fantastic program.


Really, Java programs are huge memory hogs in my experience, and Python programs are significantly easier on memory, and faster to boot.  When there are multiple programs that do the job... I will usually opt for a native compiled version first, then a python version, and Java as my last resort.  I try to avoid .NET and VB.

---

### Post by Flubs4u on 2007-01-12
I was loooking at using Jedit.  I'd forgotten about Eclipse, my laptop (which I'll be doing most of the coding on) only has 256 RAM, so I may just stay away from it.  From what I can tell Jedit is just a text editor with highlighting for java, but I don't see anything about a compiler.  Does java even need a compiler?  My programming experience is mostly limited to C++ in a visual studio environment, so I appreciate all your help in broadening my horizons in terms of development tools.

Thanks!

Flubs

---

### Post by Wybiral on 2007-01-12
> You know, I'm sorry. I know there's a lot of Python evangelism around here. But I am going to perpetuate that just a little more. And it's because it really is a good language. I've used many cross-platform applications. Java and Python are two fairly common choices.

Eclipse: Written in Java. Hogs memory like you wouldn't believe.

Azureus: Written in Java. Very well featured, but hogs memory. I use it because it has a couple of features I can't get anywhere else.

Bittornado: Written in Python. Fast, and doesn't hog a lot of memory.

Picard Tagger: Written in Python with WxWidgets. Fantastic program.


Really, Java programs are huge memory hogs in my experience, and Python programs are significantly easier on memory, and faster to boot. When there are multiple programs that do the job... I will usually opt for a native compiled version first, then a python version, and Java as my last resort. I try to avoid .NET and VB.

I agree... I've tried eclipse and it makes my computer practically stop ticking...

Java requires loads of memory to run (partly due to the JIT)

Another examples is Frostwire... I can hardly do anything when it's running. Someone should rewrite it in C or Python.

---

### Post by Flubs4u on 2007-01-12
Grey:

I've actually used a bit of python and in all cases I've been really impressed with how powerfull it is.  I've personally never gone through the process of actually making a stand alone program in python, all my experience has been mostly educational use running things through the translater (or whatever it's called, I can't remember at present.  EDIT: Interpreter...just took me a while to remember).  But as long as you can make a stand alone program that will run on multiple platforms I'm definately open to it.  Do you know how good or bad the python libraries for displaying images are?

---

### Post by Grey on 2007-01-12
Python can actually use C libraries IIRC.  So you shouldn't have a problem using the image libraries.  It's a very full featured language.

---

### Post by Wybiral on 2007-01-12
And anything python doesn't have (which isn't much) you can whip up a quick module for in C (viper in my signature is a python module I wrote, its open source so if you ever want some basecode and a makefile, it's there)

---

### Post by Flubs4u on 2007-01-13
sweet, thanks for all the suggestions guys.  I've picked up a copy of the ebook 'Dive into Python.'  Any other suggestions?

---

### Post by Wybiral on 2007-01-13
Pmasiar has some good advice on python in this link: [http://www.ubuntuforums.org/showthread.php?t=333867](http://www.ubuntuforums.org/showthread.php?t=333867)

It's three/four post's down.

---

