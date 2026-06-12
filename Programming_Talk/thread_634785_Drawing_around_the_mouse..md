---
title: "Drawing around the mouse."
date: 2007-12-08
forum: Programming Talk
---

### Post by NJDubois on 2007-12-08
I am wondering how to write a program that will draw a circle around the mouse when a key combination is pressed.  So, shift+enter will draw a small box around the mouse, and depressing the keys will make it go away.

I'd like to make my own kind of panel, that pops up at the mouse. I want to do this to see if I can drop having panels on the edge's of the screen.  

I'd like to start by just creating that circle around the mouse, with in gnome, while doing day to day stuff.  

I'm hoping to be able to do this in C/C++ because I'm familiar with them. 

 If I can do it in c, what do i need to know to start developing that kind of program? 
 * wiki's
 * Librarys

 I looked at gtk2.0 but it doesn't seem to offer me what I need.  In an irc server, someone told me to look at x.org.  But couldn't find anything.

I hope someone out there in ubuntu land can point me in the right direction!!
thanks!
Nick

---

### Post by Compyx on 2007-12-08
Sounds like you need to look into [xlib]("http://users.actcom.co.il/~choo/lupg/tutorials/xlib-programming/xlib-programming.html").

---

### Post by NJDubois on 2007-12-08
Looked into Xlib.  Found a basic how to, copyed the c code, compiled it, ran it.  got a simple window, and it draws a box around my mouse where i click.  I still dont have a huge idea of whats going on, that will come with time.  What I would like to know, how to make the window transparent, and no titlebar (min max close buttons and all).  Or, could I just draw directly to the 'screens root window', and completly bypass the drawing of an acuall 'window' ?

The site i used:
[http://users.actcom.co.il/~choo/lupg/tutorials/xlib-programming/xlib-programming.html#preface](http://users.actcom.co.il/~choo/lupg/tutorials/xlib-programming/xlib-programming.html#preface)

I read some of the begining stuff, but I learn better by acually looking at the code and saying, this did this, and that did that.  And I managed to change the pixel change in events.c to draw a box from x-10, y-10 with a height and width of something like 30.  And it works.  =P

Also, I did a google search for 'create_simple_window' and was hoping to find a site that will give help on it, a basic example. related commands, definitions and so on. But no luck.

Thanks for the fast reply, you got me to stay up till HA, almost 5 am.  I have not programmed in years, and am trying to get going in linux.

Here is a brief idea of what I want to do.
If you have played nwn1 you will know exactly what i mean by radial menu.

Only, when you hit what ever key/mouse combo you want to activate it, this radial menu will appear, sorta like a donut, and your mouse will be centered over the 'main menu' or to use a windoz term 'start' button.  next at about 1 o'clock will be your quick launch bar shaped to follow the curves.  than going from top to bottom along the left will be your opened windows list.
instead of

X    X    X    X
X    X    X    X

it would be

-X
---X
-----X
------X 
-----X
---X
-X

note: ignore the "----" had to do it to space them out...  ; )
But the X's represent the start of the box stating the title of the window.

and then the clock and date with space for maybe most used of most used main menu items?  

May be make the acual donut a black, almost all transparent with neat shadows, it would look really sharp!

I really want to kill the damned panels, and I think something like this would be a close to a first step in no longer being stuck using a 2d desktop environment, to something even more 3d than the 3d cube effects... in my opinion....

Well, thats my plan, any comments or tips you can throw at me to help me on my way are greatly appreciated!

Nick

---

### Post by xtacocorex on 2007-12-08
This may seem like an out there proposition, but Fluxbox and Openbox have a menuing system that displays on a mouse click on the desktop.  I'd look at their code and see how you can improve it and make it your own.

Here is a picture of a Fluxbox style showing the menu: [http://fluxbox.sourceforge.net/zoom.php?themes/contrib/naytro_slack.jpg](http://fluxbox.sourceforge.net/zoom.php?themes/contrib/naytro_slack.jpg)

Here is the documentation on how the Fluxbox menu items are set:
[http://fluxbox.sourceforge.net/docs/en/newdoc.menuedit.php](http://fluxbox.sourceforge.net/docs/en/newdoc.menuedit.php)

---

### Post by NJDubois on 2007-12-09
I looked at Fluxbox and with what I am doing, the code would be the same idea.  Gnome and Fluxbox both would just run the menu from the x and y of the mouse.  BUT you did give me a good idea as to where I could look!  The menu code in gnome will tell me the x and y of the mouse (I love cut and paste...)  and what gnome is doing.

fluxbox was interesting, but I perfer gnome.  Thanks for your idea, and it did help!

I am working on a mock-up so I can give a better idea of what I'm looking to do.

Thanks!
Nick

* EDIT *
I did some light research into the gnome code, and I am trying to find out how to view the source code gnome, mainly the mouse right click menu part of it.  Also, I would like to view the code for the plain old panel.
How do I go about doing this?  looking up anything panel just returned stuff about applets, and right now I am not concerned with that, Just want to draw that circle, and then move up from there.

Also, Is there a way to make a window, using c/c++, transparent and an item in the notification area and not the taskbar? How could I make the window invisible and the stuff that I do on the window visible?

thanks.
Nick

---

### Post by NJDubois on 2007-12-10
my mock up

[http://www.gnome-look.org/content/show.php?content=71426](http://www.gnome-look.org/content/show.php?content=71426)

---

