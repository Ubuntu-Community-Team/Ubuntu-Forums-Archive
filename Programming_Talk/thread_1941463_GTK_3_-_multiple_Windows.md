---
title: "GTK 3 - multiple Windows"
date: 2012-03-15
forum: Programming Talk
---

### Post by anewguy on 2012-03-15
I have a feeling I may be doing something wrong, and it might be causing one of the problems I have run into.

Basically, using GTK, I have defined a main screen.  This main screen has 1 or more options on it.  When 1 of the options is selected, I use another C function to hide the main screen, define a completely new screen to handle things specific to the selection, then "return" from the function - thinking this would put me back in the gtk_main loop but with this new window.  When the new window is closed, it destroys itself and then "un-hides [shows]" the main window again.  This all seems to work fine, but I can't find anything that says if this is correct.  I almost get the feeling I should be creating a dialog of some sort and running it, assuming I can define a box for a dialog and essentially build an entirely new screen in that box.

I'm concerned about this as one of the gtk functions I am trying to use (that's it a separate thread about the topic it's used in) runs a dialog that wants the window name it belongs in - when I give it the name of the "option-selected" window it bombs out at run-time with errors about setting a parent window on a window that is already a parent or some such thing.

So, I'm thinking if I'm doing this all wrong, perhaps that is causing that problem.


basically:

main window - option "A" -> hide main window, define window "A"
main window - option "B" -> hide main window, define window "B"

etc..

I guess one could think of the main screen as sort of a menu.  In fact, initially I set it up as a menu, but with the way Unity handles menu placement on the screen it made no sense at all.  And......the entries for the menus still defined separate windows.

If this makes any sense (especially if someone understands what I'm trying to do and sees that how I'm doing it makes NO sense ;) ) your help would be greatly appreciated!

Thanks in advance!
Dave ;)

---

### Post by anewguy on 2012-03-16
Please forgive a bump 2 hours early - I'm going to be gone until later this evening and was hoping someone would be able to provide some sort of guidance on this.

Thanks in advance!

dave ;)

---

### Post by anewguy on 2012-03-17
No answer? Hummmmmm......

I hope (but find itquite hard to believe given the audience) that nobody has an answer. If it's a personal thing, please just say so and why, as I thought this was a legitimate question in a forum I hoped worked the same as the other Ubuntu forums.

BTW - the previous post says "1 day ago" and at the current moment this one says "12 hours ago", but I assure you 24 hour had passed.  The previous "expired" if you will on Saturday, and this was made Saturday after that.  Too bad everything is by hours or by days so everything would be judged the same.

---

### Post by anewguy on 2012-03-18
I have found no references in the documentation or on the net anywhere for how to do this, so I'm going to assume I'm right.  Hide a screen, define a new one so actions can only be taken on it's functions, and "return" so you're just back in the gtk_main loop, just with a different screen showing.

Since no replies, closed.

---

### Post by r-senior on 2012-03-19
I know you've closed the thread but your hide-window/show-window approach sounds unnecessarily complicated to me. It sounds very much like a custom dialog.

I see your program as a little bit like Glade, but instead of adding UI components, your program is adding CSS components. Glade provides a palette on the left as a "menu" of components. Then it uses a variable-width panel to configure properties for the components that have been added but also provides a dialog that does something very similar to what I think you want.

---

### Post by anewguy on 2012-03-19
Perhaps more pictures are worth a thousand words.

First the opening "menu" page.  As things grow, there will be other options added to this page.

Second, the screen that shows after the selection from the main screen.

Everything I've read on dialogs indicate using a dialog box, and there is only 1 box widget that can go in the dialog.

Since gtk_main() is basically just a big signal handler that runs in a loop, it would seem to me what it is working with in terms of windows is rather unknown to it.  At it's most functional layer it knows I have active buttons, etc., defined as "x" with signal handlers of "y".  If I use a signal handler function of 1 window to create actually hide that window and show another before returning, all I've done is defined a new set of buttons and signal handlers - gtk_main doesn't care.

I don't use Glade.  I don't want another layer between me and what is happening until I understand what is happening - just my background and in the long run it helps with using the "tool" better.  Glade is just a layer on top of GTK - the end result is still GTK, just hidden from you by the Glade calls in your program.

Works - make sense to me - and as best I can tell gives me more control over what I want to do.

Right now to me this is done deal.  My problem at the moment it getting access to just font names or families without the extras that the GTK call adds.  I want to control those separately, just as in many many other programs, including the reply window I'm using now.

Thanks
Dave ;)

---

### Post by anewguy on 2012-03-19
Jeez......then I go and forget the images!

There aren't enough "slots" for files to include the font selection screen.

I have color selection working.  Font selection pops up the window that GTK shows - but doesn't give me individual control of showing/controlling options.

I store all of this information internally, then *if* the user wants to save the changes when they are done I update the css file at that point.  The css file doesn't include font selection, color selection, etc. - I do that in my program.  If you are familiar with the Gnome Shell (not just Gnome as we install with Ubuntu, but the package Gnome Shell) you can find the gnome-shell.css file.  That is the file I am writing the editor for.  Currently users are having to manually edit that file and input hex values for colors, etc., try it, modify it, etc..  With the program, as an example with colors, they can select via the color wheel, see the colors, see the gradients, see the transparency.

If anyone has an existing program to do this, or a better way than what I'm trying to do, please step forward and do it.

Dave

---

### Post by anewguy on 2012-03-19
Maybe I can attach the screen shot of the default font selection screen from GTK using another reply.....

GTK gives no control over hiding font size, weight, etc., from this selector and letting you use them separately.  In addition, there appears to not be any function that will do so.  The closest I have found is an Xlib call to return font names.

---

### Post by r-senior on 2012-03-19
I didn't mean you should use Glade, I saw Glade as an example of a similar interface to what you are trying to achieve, i.e. with it's palette of controls analagous to your palette of CSS styles.

Function to return list of fonts using Pango added to your other thread:

[http://ubuntuforums.org/showthread.php?t=1941461](http://ubuntuforums.org/showthread.php?t=1941461)

---

### Post by anewguy on 2012-03-19
Hey, thanks!! I'm sorry I misinterpretted!  You've been my only help all along!  I did see the Pango stuff you posted for the font "problem" and I will be trying that out a little later either tonight or tomorrow.

Thanks again, and sorry for misunderstanding!

Dave ;)

---

