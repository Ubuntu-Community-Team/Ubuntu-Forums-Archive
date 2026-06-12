---
title: "3D graphics and GUIs"
date: 2006-02-18
forum: Programming Talk
---

### Post by Houman on 2006-02-18
Hi there;
I have recently moved to linux comepltely. before I used to do my programming stuff on windows, using C++ and the good old windows API, things were pretty simple, using the MFC library I could do graphics stuff, do the GUI stuff and pretty much everything that a programmer needed was done using the windows API.

Now that I have moved to linux, I need to do some graphics programming for a project. I need a small GUI  that enables the user to see a cloud of points in 3D after a button is clicked. In widows I would have known how to do this; but in linux, I have been googling around and I am getting more and more confused: qt, gtk, motif, athena, opengl/glut, sdl... What do i need to do graphics programming? which is the most popular library?

also SDL seems to be a good choice for 3D stuff, but how would i handle the GUI? can i use SDL and GTK libraries in the same file?

any advice is very welcomed, I am very much overwhelmed by all the libraries available;

Houman

---

### Post by dee.dw on 2006-02-18
Hello! I would use QT or wxWindows for the GUI and OpenGL for the 3D-part. I have programmed something in QT and OpenGL and it won't be no problem to send you the code as example. (Maybe as example for bad commenting also! ;))

Advantage of wxWindows is that it's free for Linux and Windows, so you could probably port your code to another system. Or better: You could program it under windows and then compile it under Linux. ;)

Greetings, Dee

---

### Post by nagilum on 2006-02-18
I'm not sure about the SDL and GTK+ combination, it seems that using SDL in a seperate window is quite easy but integrating it into your main window is a problem.
However there's a OpenGL extension which provides additional GTK widgets that you can integrate into your application. [Look here](http://gtkglext.sourceforge.net/) for more information and some examples.

---

### Post by Houman on 2006-02-18
thank you dee and nagilum;

I have another problem that i forgot to mention; my supervisor has solaris :( and i need to be able to run this stuff on his computer as well; GtkGLExt looks like what would be the best option, but how would I be able to run it on solaris?

I think i should use the lowest common denominator graphics library of all linux distros if i want to have portability to those sun workstations (and even then im not sure if it would work). I think the lowest common denominator is the X Window's Athena widgets , but I have been advised against using that because it is too low level, how bad is it compare to gtk? i mean in terms of difficulty? I need to be able to rotate some graphics and also be able to show bitmaps, (I dont need 3D API per say, if I can do simple 2D graphics I can create the 3D stuff by some simple geometry (project into some plane, cut one axis...) )

and is the athena widget sets truly portable to solaris?

thanks again;
Houman

---

### Post by dee.dw on 2006-02-18
Solaris? Hey great... I did my stuff in QT and OpenGL on a Solaris machine too. (There was nothing else in our faculty... ;)) It takes some time to compile QT there (Don't forget to include OpenGL-support. I made this mistake only one time. It took me 4 hours... twice!) but this was no problem.

Here's the link to my project: [Zip](http://www.cyskat.de/dee/progs/dna-v13.zip) and [Help-File](http://www.cyskat.de/dee/progs/dna/index.htm). To be honest: I didn't use the full potential of OpenGL because I only show some 2D-objects.

Edit: Ah, I forget to say that I only know QT and OpenGL and I do not know if there are other languages that would be better for your task. Maybe someone else can say something about Athena. :)

Greetings, Dee

---

### Post by Houman on 2006-02-18
hi dee;

thank you so much for the help and the links! I just had one mroe question, should there be somethign installed on those solaris machines? like the qt-devel packages or somethign? 

I mean I doubt if i use qt and build my source I will be able to execute the binary on solaris because they dont have those libraries installed,

thanks again and i do appreciate the help, looking at your code right now (nicely written and commented, not like my spaghetti code)

regards;
Houman

---

### Post by dee.dw on 2006-02-19
You should install the pakackage "qt3-apps-dev" and all dependencies for it. Additionally you may need "libglut3-dev" to be installed (Libraries for GL and GLU depend from qt and will be installed before!)

> I mean I doubt if i use qt and build my source I will be able to execute the binary on solaris because they dont have those libraries installedNo, without the devel-package you wouldn't be able to build the source at all. (In case of static linking what I prefer! :))

> nicely written and commentedAre you sure you're looking at my code??? ;) If I take a look at the code today I think there are way to less comments in it.

Do you know QT-development? I only could recommend the doc sites of [http://www.trolltech.com](http://www.trolltech.com). They are very good and helped me! Otherwise there are also a lot of books about QT you can buy. Same for OpenGL...

Greetings, Dee

---

### Post by Houman on 2006-02-19
hi dee;

thanks for the tips; And no I dont know any GUI libraries in linux, so far I have done everything on windows (because my supervisor said so) but now that I have a new supervisor the first thing I did was format my windows and switch to  linux completely ( i had wanted to do that for a while), so anywyas I am at the beginnign of my journey into linux programming :)
I thought I should use GTK because I was googling around and I read about the licensing stuff about qt libraries, that you have to pay if you use it in a commercial app, and that kind of turned me off, but if you think it goes better with opengl I will give it a shot;

and as far as your code, I think you have just the right amount of comments, I am not a good programmer but the few books I have read always suggest to keep comments as few as possible and instead make the code readable, too many comments is redundant and creates clutter, as long as you comment a block of code and for instance you say what their purpose is i think thats enough, and you have done that :p and plus your code is readable, 

anywyas, thanks again
Houman

---

### Post by dee.dw on 2006-02-19
> but the few books I have read always suggest to keep comments as few as possible and instead make the code readableYou read the wrong books. ;) No, of course it is very good to call a class (or variable) not just "CS" instead of "CircleSpline" but today I use a lot more of code. Almost every line has a detailed description what I have done because after a year I often do not understand anymore what I've done these days. :) (Of course some for-loop has no description. *g*)

If you need any help in QT and OpenGL I try to help although my know-how in these languages is a little bit out-of-time.

One hint: If you need to distribute the result, resell it or something like this without giving the code away, I wouldn't use QT because of the licensing model. Otherwise if you program open source everything is fine. :)

Greetings, Dee

---

