---
title: "I need help with an idea for a new 'start menu'"
date: 2008-04-11
forum: Programming Talk
---

### Post by NJDubois on 2008-04-11
I posted a while back trying to get some information about mouse location's and stuff so I could have a circle shaped menu.  But I could not figure out what was going on and got very little replys to my post.

SOOOOOOOOOOO

I made the basic idea of what I'm trying to figure out how to do in Visual Basic 6.0.  I know, WINDOZ =(   But i'm good with vb and can do just about anything I need in it.

What I did in this program that I want to do for linux.

First I wrote a simple program that when the user moves the mouse left to right (I call it shaking).  I measure the time between when the mouse x stops getting smaller and the mouse x stops getting bigger and when this time is lower then a set number so many times the menu pops up.

I did some basic work on this menu form.  It reads from a text file that a button on the start up form creates.  This text file simply has notepad.  The menu form has only one button and thats to run notepad (all read from the text file... )

The menu form also auto hides if the mouse is not over the form, or is over the form and inactive for a set amount of time.

there are a few problems.  For some reason when i try to show the form and put it at the mouse x and y it scales it so its really only in the upper right of the screen, I simple multiply the x and y nnumber by 15 to get it closer to the acuall position of the mouse.  Don't know why it does it, don't care.  Why?

I want this in linux.  I would like to build my own menu and be closer to getting rid of the icons.  I'd like control over what, how and where items are displayed.  I have yet to see a menu thats up to my standards and I really don't like any out there.  Except for Raptor...which doesnt seem to be moving from just an idea to an acual project.

I have attached all source files for the vb6.0 program as well as an exe if you don't have vb6.0 OR don't want windoz.  Hum...might be able to run it in wine.  donno.

Note :  I feel that it is in general a bad idea to run any exe downloaded off the internet, and even though I know my code is clean I still strongly recommend reading and reviewing every line of code in any program ever downloaded!

What I need is someone to code this for linux.  If someone coded this in a neat, labeled way I could easily, or i hope so at least, be able to go in and change what i want re work this or that and make my menu.  I learn best by reading example text, and all the examples i find get kind of crazy!  So please, anyone, someone!!  

Thanks for any and all help!!!!

Nick

[EDIT] The exe has been removed.

---

### Post by LaRoza on 2008-04-11
> **NJDubois said:**
> 
I have attached all source files for the vb6.0 program as well as an exe if you don't have vb6.0 OR don't want windoz.  Hum...might be able to run it in wine.  donno.

Note :  I feel that it is in general a bad idea to run any exe downloaded off the internet, and even though I know my code is clean I still strongly recommend reading and reviewing every line of code in any program ever downloaded!


Reading the code won't help. That .exe could be anything.

It doesn't run in Wine, and this is a programming forum, so you can post the or attach the code if you want, but don't attach programs that can't be verified.

---

### Post by slavik on 2008-04-11
how about a screenshot?

edit: my understanding is that you want to do something that is called "commo rose" in battlefield2 ([http://guidesmedia.ign.com/guides/819222/images/image040.jpg](http://guidesmedia.ign.com/guides/819222/images/image040.jpg))

---

### Post by NJDubois on 2008-04-11
If you look at the mock up I posted a few months ago you get an idea of what I am aiming for.

[http://www.gnome-look.org/content/show.php?content=71426](http://www.gnome-look.org/content/show.php?content=71426)

Think more nwn1 then battlefield.

---

### Post by NJDubois on 2008-04-12
Is there anyone that can help me?

---

### Post by lnostdal on 2008-04-12
with what? what do you have at the moment? where are you stuck?

edit:
if you do not have anything, start with the gtk+ tutorial .. then take a look at the gdk api .. then possibly xlib stuff

---

### Post by YetAnotherNoob on 2008-04-12
Sounds like an interesting project. But I think you should think about it before diving in. It will probably not be as easy as you would like. I recommend doing some web research.

You could research:
* a programming language eg: Python, C++, C#
* a graphics library.  maybe try a few tutorials with various libraries to find something you like.
* documentation on how to programmatically access to the various gnome/kde desktop elements you want to display in the radial menu. Icons, Links, etc will probably need to be dynamically built and updated.

There are other projects out there that do similar things with the desktop.  You might try having a look at their source and figuring out how they work. Avant Window Manager (AWN) comes to mind.  AWN is completely different to a radial menu, but similiar programming concepts may be required.

happy hunting

---

### Post by NJDubois on 2008-04-12
I am very fluent in c/c++, just rusty.  I have researched gtk2.0  and have a basic idea of programming with it.



I got the basic hello world button tutorial up and running, was able to change the button to a label, but can not seem to figure out or find somewhere that explains how to change the text in a label once its been setup. 

Also did some work using tables to setup a label and a button.  I don't understand why you cant just assign an x and y value for the location that you want your widget placed but I can deal with it.  

Where I got stuck was reading the mouse posistion on the screen. 
I use

gdk_window_get_pointer(window, &x, &y, NULL);

If i understand right, it will only give x and y in relation to a window.  Which is why I believe that when I try to read the position without a window displayed I get nothing.  



Being able to change a label would help me get a better understanding of whats going on, I will start with asking about that.  I have done search's on this subject, and get a few differnt ways of doing it.  They all look differnt, which makes me think that I'm in the right area, just not the right language maybe?

Another question.  I had a while loop inside main() that seemed to work, seemed to exit correct but after when i tried to display the window I got nothing.  I tried a few things and sometimes the program seemed to just end while other times it was still running, i knew cause i had to end it in the task list, but no window ever displayed.

As I said, I have a good understanding of c++, i knew more than my ap computer science teacher did in high school, but that was a few years ago.  I learn best by example and if someone could whip out a program with a window and a label on it that displayed the x and y of the mouse it would do wonders for me.

As for anything beyond this, such as icons.  I'll worry about that next.  I will take it step by step and make sure I have an understanding of whats doing what and why, it is after all how I learn.

Thanks for all the posts, and I look forward to whats next =P

Nick

---

### Post by NJDubois on 2008-04-12
And no reply on my VB source code?  I understand that this is a linux forum, but ya gotta see it.  I think its a good idea and could add another great function to the mouse and eleminate the need for a start icon, with completion of the whole project could eleminate the need for panels with running programs clock and all.  This could free the desktop of its 2d nature and open up linux to complete 3d environments where our icons are acual objects in side a world of our choosing, from a small deserted island to a city block.

---

### Post by LaRoza on 2008-04-12
> **NJDubois said:**
> And no reply on my VB source code?  I understand that this is a linux forum, but ya gotta see it.  I think its a good idea and could add another great function to the mouse and eleminate the need for a start icon, with completion of the whole project could eleminate the need for panels with running programs clock and all.  This could free the desktop of its 2d nature and open up linux to complete 3d environments where our icons are acual objects in side a world of our choosing, from a small deserted island to a city block.

There is a windows desktop project that is meant to emulate a real desktop. I forget the name though. It is pretty cool (but not really what I would use)

---

### Post by lnostdal on 2008-04-12
> 
l, but can not seem to figure out or find somewhere that explains how to change the text in a label once its been setup.


[http://library.gnome.org/devel/gtk/unstable/GtkLabel.html#gtk-label-set-text](http://library.gnome.org/devel/gtk/unstable/GtkLabel.html#gtk-label-set-text)

> 
Also did some work using tables to setup a label and a button. I don't understand why you cant just assign an x and y value for the location that you want your widget placed but I can deal with it.


[http://library.gnome.org/devel/gtk/unstable/GtkFixed.html](http://library.gnome.org/devel/gtk/unstable/GtkFixed.html) .. edit: but you probably want to escape the whole container/layout widget idea

> 
w. Which is why I believe that when I try to read the position without a window displayed I get nothing. 


[http://tronche.com/gui/x/xlib/window-information/XQueryPointer.html](http://tronche.com/gui/x/xlib/window-information/XQueryPointer.html)

here are some stupid/silly gtk examples:
[http://laptop.nostdal.org/~lars/programming/c/gtk-helloworld.c](http://laptop.nostdal.org/~lars/programming/c/gtk-helloworld.c)
[http://laptop.nostdal.org/~lars/programming/c/gtk-mouse-button.c](http://laptop.nostdal.org/~lars/programming/c/gtk-mouse-button.c)
[http://laptop.nostdal.org/~lars/programming/c/gtk-threads.c](http://laptop.nostdal.org/~lars/programming/c/gtk-threads.c)
[http://laptop.nostdal.org/~lars/programming/c/gtk_thread_progressbar.c](http://laptop.nostdal.org/~lars/programming/c/gtk_thread_progressbar.c)

maybe you should consider hiring someone if you don't wanna bother learning this crap .. tbh. you don't seem willing to put in the effort required .. i mean; i found these links after 15 secs of googling(#1) ...  just; never mind .... forget it ..  even if i supplied you with a working example (should i?) you still wouldn't get it .. go ahead .. prove me/us wrong by showing me/us a good start


#1: here's how .. you know what you need, right;

* gtk
* gdk
* xlib

..combine this knowledge - or these words with the word "API" or "reference" .. then google .. then apply your c/c++ skills (i read something about that somewhere in there i think .. i didn't quite pay attention) .. and you're done

---

### Post by NJDubois on 2008-04-12
int x,y,cnt;
    char str[10];
    cnt=0;
    while(cnt<100)
    {
      gdk_window_get_pointer(window, &x, &y, NULL);
      sprintf(str, "%d", x);
      gtk_label_set_text(label,str);
      cnt++;
    }

I didn't post the whole program.  label is a gtk label and window is a window.  Every line of code works great except for this.

Why does this code output a -10 digit number instead of x ?

Also, this is where my memory fails me, is there a better way to output the mouse x,y with out a loop?

---

### Post by NJDubois on 2008-04-12
I bookmarked my forum post and didn't notice the second page.  lnostdal, your post helped me out a little, but was rude.  I'm sorry I'm not a high enough level programmer for you.

I already figured out how to change the label by doing research.  All I have done has been done by doing research.  Research research research.

the only usful part of your post = XQueryPointer

I am still unable to find an example that use's this to output the x and y location.

I posted here in the first place because I was tired of reading over lines and lines of source code, and reading the same thing on 10 differnt pages.  I was hoping for an explanation of how to do this, not an explanation on where to look to get an explanation.  I had thought that the ubuntu community was really laid back and quite nice to talk to and so far everyone has been.  I guess there is always a sour apple in the bunch.  I'll take my questions else where since I am obviously not up to the level required to post here.

---

### Post by nanotube on 2008-04-12
if you want to find the mouse x/y position on the screen, relative to the total screen, you can use the xlib library and its "record" module.

if you want an example, i use python-xlib in my pykeylogger project to detect mouse position. 

see [http://pykeylogger.sourceforge.net](http://pykeylogger.sourceforge.net)

specifically look in the pyxhook.py file which is where xlib gets used.

i suspect the basic ideas and methods will be similar in c/cpp, but no guarantees - i haven't done this in c or cpp myself. :)

about your vb code - the reason you are not getting a lot of comments on it is because one needs a windows machine with visual studio on it to actually run it... and this being a linux forum, i suspect most people don't have one on hand. so don't take it personally. :)

---

### Post by lnostdal on 2008-04-12
> . I'm sorry I'm not a high enough level programmer for you.

ppfftt .. i suck .. i wouldn't worry about me 

> 
I posted here in the first place because I was tired of reading over lines and lines of source code,


fascinating .. at this point i hope someone posts an example of what you seek, just to end this

but, wanna know something? ..  i _already_ have the source code of what you need; a widget-less application that "paints" _directly_ on the screen .. it is clean and "properly done" .. but you know what? .. i'm _not_ posting it  .. i'm keeping it to myself .. someone else will have to post something for you .. you're _not_ getting it from me .. its friggin MINE ..

..hah! .. you would of course have no interest in it anyway .. 

Laroza: or anyone .. please, ban me .. i can not endure this any longer ..... kill me now .. i want to be rude and ugly .. i _don't_ care ...... :/

---

### Post by Can+~ on 2008-04-12
> I was tired of reading over lines and lines of source code, and reading the same thing on 10 differnt pages. I was hoping for an explanation of how to do this, not an explanation on where to look to get an explanation.

There's a certain line on which you are asking a favour, and asking to do your task. I think you crossed it.

Seriously, one of this forums, is that we point you in the right direction, link here, link there, etc. But when you don't want to read source code or examples, or the documentation, then why "we" should bother? (Looks like Inostdal's head just blew up)

Oh, and if I were you, I would do a keyboard shourcut, like Ctrl+Something to run your application, rather than mouse shaking. And there's something that already works, called Gnome-Do, which summons a launcher with Ctrl+Space bar.

And if your C++/C skills are rusty,[ take a look at Python]("http://www.xkcd.com/409/"), it usually solves the problem of handling pointers everywhere.

---

### Post by LaRoza on 2008-04-13
> **lnostdal said:**
> 
Laroza: or anyone .. please, ban me .. i can not endure this any longer ..... kill me now .. i want to be rude and ugly .. i _don't_ care ...... :/

Quite. Thread closed.

(Something tells me it is a weird hour over there in Norway, and you have some strange bugs to work out in Lisp. Not to mention working with a French guy...)

@OP We are glad to assist you (or anyone) in learning, or getting things done, but no one here is going to do this for you.

---

