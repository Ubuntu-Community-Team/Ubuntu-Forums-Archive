---
title: "Top application bar disappears"
date: 2012-04-14
forum: New to Ubuntu
---

### Post by lucaluca90 on 2012-04-14
Hi everybody! I was trying to add some visual effects to ubuntu so I installed compiz and some compiz extra plugins. Everything works fine but sometimes the bar that should be at the top of each application disappears! I know this can be confusing so i prepared an image:

[http://imageshack.us/photo/my-images/210/nobar.png/](http://imageshack.us/photo/my-images/210/nobar.png/)

It doesn't happen suddenly, but something like 5/10 minutes after I turn on my computer. If I restart my computer I have the bar back, but after 5/10 minutes it disappears again. What problem could it be? Here's a list of compiz plugins I have active now (they're translated by me from italian so probably the names are not exact):

> General: GNOME compatibility, composite, openGL
Accessibility: enhanced zoom desktop
Desktop: cube desktop, expo, rotate cube, ubuntu unity plugin, viewport switcher
Effects: animations, cube reflection and deformation, window decoration
Image loading: jpeg, png
Utility: bailer, compiz library toolbox, regular expression correspondence, detection, mouse position polling, session management, workarounds
Window management: grid, move window, position window, resize window, scale window
Without category: unity MT grab handlesThank you in advance for the help!! :)
PS I'm sorry if this is the wrong place to post but I'm new in the forum!

EDIT: I forgot to say that what you can see in the image happens for all the applications, not only for the "folder application" I used to take the screenshot. Also notice that I have both the top bar (the one with the clock, user name, etc.) and the bottom application bar (I moved the left side bar to the bottom of the screen with some other plugins but it works fine). The disappearing bar is the one at the top of each window, the one with the buttons "x", "-", etc.

---

### Post by alex2e1gzy on 2012-04-14
I had this happen to me, so I moved to Gnome shell. Never turned back!
 
Sorry this doesn't help much, but I would be interested if you found what was causing this.

---

### Post by zombifier25 on 2012-04-14
try running
```
gtk-window-decorator --replace & disown
```
in a terminal.
This is the short term fix. For long term, maybe you should reset the Compiz profile.

---

### Post by lucaluca90 on 2012-04-14
> **zombifier25 said:**
> try running
```
gtk-window-decorator --replace & disown
```in a terminal.
This is the short term fix. For long term, maybe you should reset the Compiz profile.

I tried the two commands and it worked! Well, I have to launch the command every time I have the problem and I have to keep the terminal open in order to have the application bar, but it somehow works. However when I launch the commands I have these interesting messages (I probably saw them also when running compiz but I ignored them, my fault :S ):

> (gtk-window-decorator:8217): Gtk-WARNING **: Impossibile trovare il motore del tema in module_path: «pixmap», 

(gtk-window-decorator:8218 ): Gtk-WARNING **: Impossibile trovare il motore del tema in module_path: «pixmap»,

(gtk-window-decorator:8219 ): Gtk-WARNING **: Impossibile trovare il motore del tema in module_path: «pixmap»,
In english they would sound something like: "impossible to find the engine of the theme in module_path:<<pixmap>>".
Maybe this can help, these messages could be related to my problem. However I need to work with my computer so I need to fix this: could you tell me how to reset the compiz profile? It's probably not the best solution, but I need to fix this as soon as possible :)

> **alex2e1gzy said:**
> I had this happen to me, so I moved to Gnome shell. Never turned back!
 
Sorry this doesn't help much, but I would be interested if you found what was causing this.

Follow this discussion, I'll write here if I find something new! :) However I think it's something related with some bug in compiz, or I did something wrong without noticing it!

---

### Post by lucaluca90 on 2012-04-14
I fixed the gtk problem through google but it didn't fix the main problem. Then I tried with this guide I found over the internet:

[http://reformedmusings.wordpress.com/2011/05/05/howto-get-the-compiz-desktop-cube-in-ubuntu-11-04-natty-and-unity/](http://reformedmusings.wordpress.com/2011/05/05/howto-get-the-compiz-desktop-cube-in-ubuntu-11-04-natty-and-unity/)

Before doing this I found and used the command to reset compiz configuration. Until now it seems it's working fine, although I don't know why. :) It is said in the guide that changing compiz configuration often causes crashes and I can confirm that, so maybe that was the point in my problem (some crash created some problem). So that's it, you have the link I used to (I hope) solve the problem, if I'm not having trouble within some days I will put the [solved] tag on the topic :)

---

