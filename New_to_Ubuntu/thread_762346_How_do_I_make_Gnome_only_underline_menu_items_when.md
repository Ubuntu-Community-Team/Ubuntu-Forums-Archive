---
title: "How do I make Gnome only underline menu items when I press Alt?"
date: 2008-04-22
forum: New to Ubuntu
---

### Post by Alaska_Jack on 2008-04-22
I'm a mac user, using ubuntu for the first time, and I just don't like the way the menus look, with one letter underlined all the time.

Surely there must be some way to toggle this behavior?

- Alaska Jack

---

### Post by dmizer on 2008-04-22
long answer:
windows does the same thing.  the underlined letter is there to show which letter is the keyboard shortcut.  it indicates which letter to push to access the menu and menu item.  for example, while using firefox, you can access the history menu by hitting alt+s, or the file menu with alt+f.

this way you can navigate through the menus without using the mouse.  for some people this is an extremely effective time saving feature because you don't have to stop typing, remove your hand from the keyboard, find the mouse, move the pointer to the menu, and find the item in the menu.

it also gives a handy visual reference to show what the keyboard shortcut is without having to clutter the menu with each and every keyboard shortcut command.

short answer:
nope, no way i know of to turn it off.

---

### Post by Alaska_Jack on 2008-04-22
> **dmizer said:**
> long answer:
windows does the same thing.  the underlined letter is there to show which letter is the keyboard shortcut.  it indicates which letter to push to access the menu and menu item.  for example, while using firefox, you can access the history menu by hitting alt+s, or the file menu with alt+f.

this way you can navigate through the menus without using the mouse.  for some people this is an extremely effective time saving feature because you don't have to stop typing, remove your hand from the keyboard, find the mouse, move the pointer to the menu, and find the item in the menu.

it also gives a handy visual reference to show what the keyboard shortcut is without having to clutter the menu with each and every keyboard shortcut command.

short answer:
nope, no way i know of to turn it off.

Thanks dmizer! Wow, all the way from Japan too! That is way cool.

Yeah, I understand what the underlines are for. What I was hoping for was an option where the underlines would only appear once the alt key was pressed. It is a purely cosmetic thing, but I am a mac user, and the menus just look cluttered to me with all those underlines.

Thanks again for the reply... I appreciate it! Domo arigato or whatever  :^)

   - aj

---

### Post by dmizer on 2008-04-23
actually, i've been looking at this more.  i really like your idea, because you don't need to know the shortcut unless you push the alt key.  alas, searching is difficult because of how common the word "underline" is.  i did find an old thread on these forums which discussed the same issue with no resolution: [http://ubuntuforums.org/showthread.php?t=578226](http://ubuntuforums.org/showthread.php?t=578226)

the consensus seems to be an application specific hard coded feature rather than something related to the overall window manager.

you might take a deeper look at compiz, or the like, which provides more control over the look, feel, and layout of your desktop.

tonde mo gozaimasen.  hope you find something, and if so ... post it.  you're certainly not the first person to wonder about it.

---

### Post by Alaska_Jack on 2008-04-25
> **dmizer said:**
> 

tonde mo gozaimasen.

gesundheit   :^)

  - aj

---

### Post by practic on 2008-10-07
I think there is a solution that was posted here:

[http://ge.ubuntuforums.com/showthread.php?t=241868&page=52]("http://ge.ubuntuforums.com/showthread.php?t=241868&page=52")

It involves a small change to the source code of the gtk+ libraries and a recompile...so, not a simple config option, but not that difficult either.  But this thread has over 200 pages and I didn't read through it all.

Personally, I also would like to see an option to hide the underlines until the Alt key is pressed...it looks cluttered with them visible all the time.

---

### Post by damijit on 2009-02-21
Has any progress been made on this? This is something I would be very interested in.

---

### Post by orkerone on 2009-07-11
Does someone have a solution to this ? Link is broken =/

---

### Post by xionlander on 2009-08-15
Please visit this link...it has de solution...It worked for me..!!!
Cheers...
 
[http://ubuntuforums.org/showthread.php?p=7483418](http://ubuntuforums.org/showthread.php?p=7483418)

luck...

---

### Post by Houbos on 2010-03-03
Here's the solution how to disable underlining in all menus and preserve keyboard shortcuts (e.g.  CTRL+C). Works also with Global menu.

[LIST=1]
[*]Open **Terminal**
[*]type **gedit .gtkrc-2.0**
[*]insert following: **gtk-enable-mnemonics = 0**
[/LIST]
If you want to completely disable shortcuts, add also **gtk-enable-accels = 0** (don't know why would anyone want to do this.)

Source: [http://library.gnome.org/devel/gtk/stable/GtkSettings.html#GtkSettings--gtk-enable-mnemonics](http://library.gnome.org/devel/gtk/stable/GtkSettings.html#GtkSettings--gtk-enable-mnemonics)

---

### Post by andymandias on 2011-05-13
Thank you Houbos for your instructions!  You helped me figure out how to disable mnemonics.

For others who might view this thread, please be aware that disabling menu mnemonics means more than just removing underlining in menus (which is actually a side effect).  It means that you cannot access menus using the alt-key anymore.  Also, I've found that the underlines remain in some applications (e.g. Empathy 2.34.0) even though the alt-key access is removed.

---

