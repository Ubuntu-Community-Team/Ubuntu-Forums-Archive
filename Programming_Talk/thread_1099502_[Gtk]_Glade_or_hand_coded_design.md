---
title: "[Gtk] Glade or hand coded design?"
date: 2009-03-18
forum: Programming Talk
---

### Post by sujoy on 2009-03-18
Well the topic says it all. I used only glade till now, but for some tasks, adding widgets based on user choice, hand coded widgets are required.
Is there any other reason why glade should not be used? Or should we keep flexibility in mind and use glade exclusively?

What is your preference and why?

---

### Post by kknd on 2009-03-18
Right now I prefer to do all hand coded, bacause the current version of Glade 3 and the moving from libglade to GtkBuilder are currently unstable, but when it's ready, glade will rock again.

---

### Post by nvteighen on 2009-03-18
I'm not really into GUI programming, but when I do some, I like to hand-code it. Not sure why, maybe because I feel I still have to learn how GTK+ works... :p

---

### Post by jimi_hendrix on 2009-03-18
ive been told to you glade, but i dont think its needed...

i think its a good tool for discovering stuff and planning out your design...but then again its a WYIWYG editor

---

### Post by Can+~ on 2009-03-18
> **jimi_hendrix said:**
> i think its a good tool for discovering stuff and planning out your design...but then again its a WYIWYG editor

And that's bad, how?

You're building a graphic application, it's logical to have some visual feedback on things are going.

Manual makes sense when you just want to make a short window with a few buttons, but when you need various windows and popups, it can be hell.

But I'm kinda disappointed with glade, having to edit something in glade, then alt+tab (or Ctrl+Alt+Tab... or w/e) to your favourite editor to write the proper bindings gets old fast.

---

### Post by cabalas on 2009-03-18
Have to go glade on this one, the ability to change the design without touching code is a big bonus for someone like me who can change their mind about a design several times in a day.

---

### Post by Gordon Bennett on 2009-03-19
Glade - for me, it's much better for user-based design as I can see exactly what goes where and how it best fits the application/user experience as a whole, plus what Cabalas said.

And *glade_xml_signal_autoconnect()* is pr0n :)

---

### Post by days_of_ruin on 2009-03-19
I use glade for I what I can and manual for everything else.
You really can't ONLY use glade.Unless you are making a very simple app.

---

### Post by Can+~ on 2009-03-19
[http://glade.gnome.org/](http://glade.gnome.org/)

Glade 3.6.0 released

"The Python plugin

This is finally worked out into a plugin, its been around for a while now but wasnt publicly/stably released to my knowlage, what it does is allow Glade to introspect and load your python classes properties and signals and add it to the palette automatically (with the use of a one or 2 liner user catalog), documentation coming, or ask Juan Pablo ;-) "

awesome.

---

### Post by kknd on 2009-03-19
> **Can+~ said:**
> [http://glade.gnome.org/](http://glade.gnome.org/)

Glade 3.6.0 released

"The Python plugin

This is finally worked out into a plugin, its been around for a while now but wasnt publicly/stably released to my knowlage, what it does is allow Glade to introspect and load your python classes properties and signals and add it to the palette automatically (with the use of a one or 2 liner user catalog), documentation coming, or ask Juan Pablo ;-) "

awesome.

\o/. Great. I'm going to test it now!

---

### Post by Sprut1 on 2009-03-19
> **Can+~ said:**
> [http://glade.gnome.org/](http://glade.gnome.org/)

Glade 3.6.0 released

"The Python plugin

This is finally worked out into a plugin, its been around for a while now but wasnt publicly/stably released to my knowlage, what it does is allow Glade to introspect and load your python classes properties and signals and add it to the palette automatically (with the use of a one or 2 liner user catalog), documentation coming, or ask Juan Pablo ;-) "

awesome.

Whaat, I need to do an upgrade

Glade is awsome btw, I use it as much as I can.

---

### Post by BlackLukes on 2009-03-19
Glade, of course, but I'm having some [problems]("http://ubuntuforums.org/showthread.php?t=1100788") testing the 3.6 version..

---

### Post by Gordon Bennett on 2009-03-19
Just finished playing with Glade 3.6 - it looks and operates with more proness!  Aside from the odd bug (e.g. comboboxes not updating list parameters betweeen editors) it's an excellent update.  Very nice :)

---

### Post by rich1939 on 2009-03-20
> **cabalas said:**
> Have to go glade on this one, the ability to change the design without touching code is a big bonus for someone like me who can change their mind about a design several times in a day.

+1 for Glade.

---

