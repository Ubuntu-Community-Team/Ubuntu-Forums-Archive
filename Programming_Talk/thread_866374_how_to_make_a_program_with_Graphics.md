---
title: "how to make a program with Graphics"
date: 2008-07-21
forum: Programming Talk
---

### Post by Fertech on 2008-07-21
I know how to make a "hello world" program in perl C/C++ java. i want to know how to make a program with Graphics and not from the command line.

---

### Post by Kadrus on 2008-07-21
You need to use a library like GTK or Qt or Swing for Java,and have a good knowledge of the language
[Hello World in GTK]("http://library.gnome.org/devel/gtk-tutorial/stable/c39.html#SEC-HELLOWORLD")
And check this sticky that might be useful:[GUI Toolkits for Linux]("http://ubuntuforums.org/showthread.php?t=772507")

---

### Post by rlameiro on 2008-07-21
lol - too late, but any way here it goes.

I think you will need to learn a bit more than a hello world program to start on graphic/GUI programming, but you can try to use GLIDE for the GTK gui toolkit or others. You will need to learn a how to work with the toolkit.
I am a newbie programmer, and programming in python, and for my experience is from far the easiest language to start programming and also to make GUIs. I have already made some control software with python using the Tk toolkit (Tkinter in python). bottom line first learn a bit of a language, and after learn a Graphic toolkit, and with the Help of a GUI builder like GLADE/WxGLADE, or GUI builder(tkinter) etc you will be up and running.

Anyway, in this forum you have people with far more knowledge than me so don't take my reply as correct :) it is just my opinion.

P.S. - You should go the the sticky of this forum, they have a lot of info on programming and resources etc....

---

### Post by Diabolis on 2008-07-21
If you are inpatient, use a IDE that will do all the work for you. For example you can use netbeans, which lets you create a GUI by using only the mouse. After you are done playing with it, give a look at the code that it generates.

You do need to know more than what is needed for a "hello world" if you want to make nice interfaces.

---

### Post by stevescripts on 2008-07-21
Simple graphical hello world program in Perl (using PerlTK):

```

#! /usr/bin/perl

use Tk;

my $main = MainWindow->new();

$main -> configure(-title=>'Hello World!');

my $label = $main -> Label(-text=>'Hello World!', -fg=>'red', -width => 10) -> grid(-row=> 0, -column=> 0);

my $button = $main -> Button(-text=>'Quit', -width=> 8, -command => sub {exit}) -> grid(-row=> 0, -column => 1);

MainLoop();

```

Lots of other toolkits, and lots of other languages out there.

Hope you find this a bit interesting, and good luck with continuing your programming expierences!

Steve
(as is rather obvious by the links below, perl is not my first language of choice for most of my projects)

---

### Post by ceclauson on 2008-07-22
If you're programming in C or C++, usually a good place to start with graphics is the SDL (Simple DirectMedia Layer) API.  There's a good online tutorial on getting started with it here:

[http://lazyfoo.net/SDL_tutorials/index.php](http://lazyfoo.net/SDL_tutorials/index.php)

OpenGL is another library that can be used to do graphics in C/C++, but I don't have a lot of experience with that.

For Java, you'll need to have some familiarity with Swing or AWT.  I learned using the book "Learning Java" by Niemeyer and Knudsen by O'Reilly, and found it to be pretty good.  For full-screen graphics, the following link is useful:

[http://java.sun.com/docs/books/tutorial/extra/fullscreen/index.html](http://java.sun.com/docs/books/tutorial/extra/fullscreen/index.html)

but it assumes some knowledge of Swing or AWT.

Unfortunately, due to a flaw in Sun's JRE for Linux, Java full-screen graphics support is poor for Linux, so if you're running Ubuntu, you might have to stick to windowed graphics, at least for a while.  (I found this out by google searching 'Java full-screen linux' after I discovered that full screen mode didn't work on my machine).

Hope this is helpful,
Cooper

---

### Post by ceclauson on 2008-07-22
Also, I thought I'd mention that I'm currently working on a graphics library for Java.  Here's the website:

[http://edison.seattlecentral.edu/~cclaus01/sccclib/index.html](http://edison.seattlecentral.edu/~cclaus01/sccclib/index.html)

It's currently not quite done, but it should be in the next couple of weeks.

The source code can be downloaded, so it may help someone who's first starting out with graphics in Java.  The downside is that it's full-screen oriented, and so it suffers from the same problems that any full-screen Java apps suffer from under Linux, namely, tending not to run...

---

### Post by Fertech on 2008-07-22
so what is Kdevelop c/c++, assistant, disigner KDE/C++

---

### Post by rlameiro on 2008-07-22
> **Fertech said:**
> so what is Kdevelop c/c++, assistant, disigner KDE/C++

These are development program to make KDE software using the QT graphic toolkit, they are all parts of a gigantic ( well not so much) set of tools to produce kde software that include Designer as the GUI interface Designer, like GLADE. 
Bear in mind that QT graphic toolkit is not completely open source/free for all platforms, if you want to use it read the licensing terms of it as I really don't know a lot about it.

---

### Post by LaRoza on 2008-07-22
See the sticky on making GUI's.

---

