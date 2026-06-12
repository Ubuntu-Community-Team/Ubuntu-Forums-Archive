---
title: "How do I make shaped windows?"
date: 2007-09-17
forum: Programming Talk
---

### Post by BuffaloX on 2007-09-17
I've been searching several hours now (again), :confused:

But I haven't been able to find documentation for making shaped / non rectangular / free-form windows in Linux.

I'm looking for a solution for either of these languages.
C / C++
Python
Lazarus

Solution must be compatible with Gnome, and preferably also with Compiz fusion.

Any help would be much appreciated. :popcorn:

---

### Post by Wybiral on 2007-09-17
I remember theres a way to initialize a GTK window without a frame... Maybe using that with a transparent image or something. I haven't really seen it done in Gnome though (that I can think of).

EDIT:

I remember the command now: [http://www.pygtk.org/docs/pygtk/class-gtkwindow.html#method-gtkwindow--set-decorated](http://www.pygtk.org/docs/pygtk/class-gtkwindow.html#method-gtkwindow--set-decorated)

---

### Post by aks44 on 2007-09-17
What toolkit are you using?

With Qt, look at QWidget::setMask. (search term: "non rectangular" window qt)

With GTK, look at gtk_widget_shape_combine_mask. (search term: "non rectangular" window gtk)

Anyway, the results I found seem to detail the whole process quite correctly.

---

### Post by BuffaloX on 2007-09-17
Thanks for nice and quick responses.

I haven't decided on a toolkit or library yet, partly because I want this specific functionality, and hoped for some examples that could help me turbo charge into some Linux GUI programming.

I want compatibility with Gnome because that's what I use, and also compatibility with Compiz Fusion because I plan to use it, when functionality gets on par with Beryl. (It isn't yet IMO).

I think the alpha method for Python doesn't work so well, sometimes transparent  areas show the wrong background, or the background with wrong opacity when placed on a semi transparent cube with Compiz.

The gtk_widget_shape_combine_mask sounds like what I want, but a google search has turned up only questions, and no examples....

Thanx for helping me on a clearly better track than where I came from. :guitar:

---

### Post by moma on 2007-09-17
I have some shaped window (XLib XShape* + Cairo graphics on them) examples in C/C++. I just need to find them. It's late evening here so you'll get the sample(s) tomorrow.

---

### Post by BuffaloX on 2007-09-17
> **moma said:**
> I have some shaped window (XLib XShape* + Cairo graphics on them) examples in C/C++. I just need to find them. It's late evening here so you'll get the sample(s) tomorrow.

WOW cool. 8)

This Cairo thing sounds quite exciting...
Do I understand correctly, that it works directly on the X frame buffer and should work with all X11 compatible window managers?
If that is so, it is exactly what I want, but didn't think was possible.

I'm off to read about this Cairo thingy... :):guitar:

---

### Post by aks44 on 2007-09-17
> **BuffaloX said:**
> The gtk_widget_shape_combine_mask sounds like what I want, but a google search has turned up only questions, and no examples....

[http://www.advogato.org/proj/glock/](http://www.advogato.org/proj/glock/) (search result)
[http://www.brouhaha.com/~eric/software/glock/](http://www.brouhaha.com/~eric/software/glock/) (homepage)

> Glock is a simple analog clock program. It is written in C and uses the GTK+ toolkit, and optionally the Cairo graphics library.

The original purpose of glock was to have a simple demo of an undecorated non-rectangular window using gtk_widget_shape_combine_mask(), moveable with the mouse using gtk_window_begin_move_drag().

(first result for search term: **"non rectangular" window gtk** on [clusty]("http://clusty.com"), looks like you better ditch google ;))

---

### Post by BuffaloX on 2007-09-17
> **aks44 said:**
> [http://www.advogato.org/proj/glock/](http://www.advogato.org/proj/glock/) (search result)
[http://www.brouhaha.com/~eric/software/glock/](http://www.brouhaha.com/~eric/software/glock/) (homepage)

(first result for search term: **"non rectangular" window gtk** on [clusty]("http://clusty.com"), looks like you better ditch google ;))

glock is perfect, works perfectly with both gnome/metacity and gnome/compiz.
Seems like it uses Cairo, which is vector based. Which is even better for adjusting size.

It's quite late now here, so I'll have to wait till tomorrow to look at it again.
Can't wait till I get home tomorrow. :)

Oh btw, yes I probably should ditch google, I'll check out clusty for my next searches. ;)

---

### Post by aks44 on 2007-09-17
> **BuffaloX said:**
> glock is perfect [...] Can't wait till I get home tomorrow. :)

Glad I could help on a subject I don't know anything about. ;)


> **BuffaloX said:**
> Oh btw, yes I probably should ditch google, I'll check out clusty for my next searches. ;)

FWIW, for me clusty gives way better results (the relevance is not even comparable) than google for most stuff (I'd say 90/95+ % of the searches). And whenever clusty doesn't yield any relevant result, it's quite rare that google does (although it happened). The only bad side of clusty is that it really doesn't deal well with *non-english* searches IMHO.

---

### Post by moma on 2007-09-18
Here is the sample 1.

//  shape1.cpp 
//  This simple example shows how to create a shaped, borderless window. 
//  It uses only XLib and XShape* extension calls. 

The shape of the window comes from "myshape.xbm" image.
myshape.xbm is readable. It also defines 
   #define myshape_width 200
   #define myshape_height 200

The code has a draw() function which tries to draw a red, filled rectangle on the face,  but only pixels that hits the mask (myshape.xbm) are visible.

Attached: shape1.tar 

You will need the "libxext-dev" package to compile and run it.

Compile:
$ [COLOR="SeaGreen"]g++ -lX11 -lXext shape1.cpp -o shape1[/COLOR]

Run:
$ [COLOR="SeaGreen"]./shape1 [/COLOR]
---------

more to come.

---

### Post by moma on 2007-09-18
Here is the sample 2.

// shape2.cpp
// This example shows how to create a shaped, borderless window by drawing the shape runtime.  Again, the code uses only XLib and XShape* extension calls.

The draw() function draws first the shape on the mask bitmap, then it draws the same figure on the window.  

Attached: shape2.tar

You will need the "libxext-dev" package to compile and run it.

Compile:
$ [COLOR="SeaGreen"]g++ -lX11 -lXext shape2.cpp -o shape2[/COLOR]

Run:
$ [COLOR="SeaGreen"]./shape2[/COLOR]

You can easily make the shape (window) to remold, rotate, move etc.
---------

Next> A tiny cairo sample.

---

### Post by BuffaloX on 2007-09-18
> **aks44 said:**
> Glad I could help on a subject I don't know anything about. ;)

FWIW, for me clusty gives way better results (the relevance is not even comparable) than google for most stuff (I'd say 90/95+ % of the searches). And whenever clusty doesn't yield any relevant result, it's quite rare that google does (although it happened). The only bad side of clusty is that it really doesn't deal well with *non-english* searches IMHO.

Thanx you have been a tremendous help, I also tried clusty and it seems very good. I'm kind of ambivalent about google, so it's very nice to have a good alternative. I've set it as default it will very likely stay default. :)

> **moma said:**
> Here is the sample 2.
$ [COLOR="SeaGreen"]./shape2[/COLOR]

You can easily make the shape to remold, rotate, move etc.

Next> A tiny cairo sample.

That is so cool, I had a slight problem with a broken terminal, which thankfully is fixed now. So I've only had time for a quick glance at the code, it is very easy to understand. :)
Both examples works perfectly, I've tried all the standard stuff to check if the transparency actually works OK. And there are absolutely none of the annoying symptoms of faked transparency, either in Metacity or Compiz.
The fact that it is possible to animate the window is amazing.
I can't wait to play with that, it is the next level of the desktop IMO.

Looking forward to your Cairo example, I tried glock yesterday, glock is vectobased. Which makes it extremely convenient for resizable windows.

MAN I love Ubuntu. :)

---

### Post by moma on 2007-09-18
Re-hello,

I re-uploaded the shape2.tar because the code had some old comments. 
----

I have also tried some Cairo-Gtk2 clocks. Most of them are dependent on a composition-manager such as that Compiz has or the X's built-in composition system.  Often, you will see a black window behind the clock if no composition-manager is running.

---

### Post by BuffaloX on 2007-09-18
I grabbed the new shape2 demo thanx ;)

glock works both with and without compiz.

[http://www.brouhaha.com/~eric/software/glock/]("http://www.brouhaha.com/~eric/software/glock/")

Cairo clock is much prettier, but I think it's basically the same methods, and it doesn't work without compiz.
I prefer glock because it's more universal.

I don't have KDE ATM, but could be fun to see if shape1, shape2 or glock work in KDE. If they do, I suppose they'll work on almost any Linux windows manager.

---

### Post by aks44 on 2007-09-18
> **BuffaloX said:**
> I don't have KDE ATM, but could be fun to see if shape1, shape2 or glock work in KDE. If they do, I suppose they'll work on almost any Linux windows manager.

Honestly, I'm too lazy to download the whole -dev headers just to compile glock... But if you post a pre-compiled binary I may be able to test it (I already have the GTK+ binaries installed). ;)

---

### Post by BuffaloX on 2007-09-18
> **aks44 said:**
> Honestly, I'm too lazy to download the whole -dev headers just to compile glock... But if you post a pre-compiled binary I may be able to test it (I already have the GTK+ binaries installed). ;)

I wasn't thinking about recompiling for QT (KDE)
That would probably require a rrewrite of the program, and I don't plan to program for KDE. But If it works it would be a nice side effect. 

moma has been so kind as to include precompiled executables for shape1 and shape2. Which doesn't seem to have any GTK+ dependencies.

Glock on the other hand clearly has GTK dependencies, But maybe KDE handles GTK+ better than Gnome handles QT based apps?

I was just being curious. :mrgreen:

---

### Post by aks44 on 2007-09-18
> **BuffaloX said:**
> But maybe KDE handles GTK+ better than Gnome handles QT based apps?

AFAIK KDE has no problems handling GTK+ (I have several such applications, all working fine).

As for moma's examples, they display perfectly (just a question: are they supposed to be moveable? I can't move them, even with ALT+drag...).


But I guess you can safely assume that this kind of code will work on KDE. :)

---

### Post by BuffaloX on 2007-09-19
Thanx for trying them out with KDE. :popcorn:

No they are not supposed to be able to do anything, :razz:
they have no handlers for movement, which has to be done manually, because they lack a title bar. (which is what I want)
I don't know why alt + mouse drag doesn't work.
My knowledge of the inner works of Linux is very limited.

I wonder why this functionality isn't used more for skinnable programs in Linux?

Thanks for all your help guys. :guitar:

---

### Post by moma on 2007-09-21
Re-hello,

I promised to show an example of a shaped window with Cairo-graphics, but first, I need to learn more about the XShape* functions.  I need to learn

Howto create a shaped, borderless main-window that has shaped, borderless child windows (non-rectangular child controls).  Do I need to transfer the sum of child-windows' masks to the main-window or what?

WIll now visit [news:://comp.os.linux.x]("news:://comp.os.linux.x") and see what they say. 

XShape* functions: 
[http://linux.die.net/man/3/xshapecombinemask](http://linux.die.net/man/3/xshapecombinemask)

So long....

---

### Post by BuffaloX on 2007-09-21
Cool :)
Cairo seems like the next generation in gui design.
Personally I think I need to understand X11 more first,
and maybe I'll go for Cairo and OpenGL for the ultimate GUI, thats where I believe things are heading ultimately.

atm I'm reading about X11 in general.

Had some problems compiling most stuff, since I'm quite new to all this.
Last I did any C programming was on the Amiga back in the 80's.

All the years with Windows kind of killed my interest in programming. :oops:

Good news is i found code::blocks which seems really great.
Now I just need to make it work for "existing projects" since there's no wizard for X11. Works great for SDL though.
I have figured the correct paths for the X11 includes.
So I can compile stuff manually....

I feel like such a baby right now, having to start almost from scratch.
But things are beginning to look up, very much thanks to the help I got here.  ;)

I hope that in a couple of days I can make "real" or "real small" programs.
I'm not sure if I should learn C++, I tried it in its early days, and absolutely hated it, but now I realize that what I tried back then, wasn't "real" C++, because standards had not been specified yet.

PS
The size of the binaries of X11 programs is amazing, some of the demos I've compiled are less than 10kb.
shape2 is slightly bigger than average, maybe because it's C++?
I haven't even read one single line about how the compiler works.

All in all I'm impressed with everything: Ubuntu, the gnu compiler, code::blocks, X11, and last but not least you guys.

---

### Post by moma on 2007-09-22
Hello,

> **BuffaloX said:**
> Cool :)
Good news is i found code::blocks which seems really great.
Now I just need to make it work for "existing projects" since there's no wizard for X11. 

To create XLib (X11) project:  Create first a Console Project via the wizard and set the link libraries and include directories in the Project -> Build options... dialog.
----------------------------------------------

Here is a complete Code:.Blocks project of the earlier Shape2 example.

Download the project from 
[http://www.futuredesktop.org/cb/shape2-project.tar](http://www.futuredesktop.org/cb/shape2-project.tar)

Start Code::Blocks IDE and open the project (shape2.cbp) via the File -> Open menu.

Then take a look at the settings in the Project -> Build options...  dialog.

The library "Linker settings" should be set like this
[http://www.futuredesktop.org/cb/CapturaEcra.png](http://www.futuredesktop.org/cb/CapturaEcra.png)

The code must link to following libraries
-lX11     (libX11.so)
-lXext    (libXext.so)
-lcairo    (libcairo.so)

The include file location (under compiler options) should be set like this
[http://www.futuredesktop.org/cb/CapturaEcra-1.png](http://www.futuredesktop.org/cb/CapturaEcra-1.png)

-I/usr/include/cairo 

Note: As you can see in the pictures, I've selected the project name "shape2"  in the upper left list. It means that the settings will be common to both Debug and Release compilations. Of course Debug and Release can have their own options too.


I have added the Cairo library (-lcairo) and Cairo's include files location to the project even the code does not (yet) make use of Cairo graphics.

Keep going :-)
-----------------------------------------

EDIT: I got a short answer to my guestions on comp.os.linux.development.apps.
See: [http://groups.google.com/group/comp.os.linux.development.apps]("http://groups.google.com/group/comp.os.linux.development.apps/browse_thread/thread/16413b654252f720/b77794e72f2a0645#b77794e72f2a0645")

---

### Post by BuffaloX on 2007-09-23
Great
Thanks for your code::blocks guide.

I&#314;l have a look at it immediately.

I will try to make a wizard for X11 in code::blocks, so I don't have to set up compiler and linker stuff each time.

I read the thread you started about child windows.
I may very soon run into that problem myself, but I haven't started real coding yet. I hope you have better results on [news://comp.os.linux.development.apps](news://comp.os.linux.development.apps),

Now to work... ;)

---

### Post by BuffaloX on 2007-09-24
Just to clarify the above.
moma Your codeblocks project works fine,
I just think it could be cool to have an X11 wizard with logo and stuff. 8-)

It turned out to be quite a bit more difficult than expected.
But I think I got it figured out.
Unfortunately it's too late to finish it today, but I'm confident that it will be finished tomorrow.

---

### Post by natureday on 2007-09-24
See the gtk.window_set_default_icon_list() function to set the icon for all windows in your application in one go.

---

### Post by BuffaloX on 2007-09-25
Got the X11 wizard working for Code::blocks. :biggrin:
Turned out to be pretty easy, I just modified the OpenGL example.
It won't work in Windows, but who cares? :p

Coming next will be learning more about X11 in general.
And probably some playing around with it... :)

PS:
moma How do you make attachments to posts in this forum???
Shape1 and shape2 are marked as attachment to the thread.
That could be enormously helpful sometimes
Like if somebody would want the code::blocks wizard for X11.

---

