---
title: "2 noob questions (deskbar + compiz)"
date: 2008-07-16
forum: New to Ubuntu
---

### Post by pound_forthesound on 2008-07-16
I've seen in some screenshots, the deskbar applet actually puts a search box directly onto the panel - on my laptop (ubuntu 8.04) it appears as just an icon, and a seach box pops up when I press alt+f3, I was wondering how I can change that?  To show what I mean, I want it to be like this:

[http://browserbookapp.sourceforge.net/deskbar-2-14-screencast.html](http://browserbookapp.sourceforge.net/deskbar-2-14-screencast.html)

Except I can't seem to find out how, I have version 2.22.3 installed.  My second question, is when compiz is enabled, how do I make my inactive window borders _not_ semi-transparent? I've had a look through ccsm and can't seem to find it (I'm not using emerald btw).

Thanks in advance, Harry

---

### Post by appi2012 on 2008-07-16
I'm not sure how deskbar can be set to be like that, but you can set it to "stick to panel: (under the general tab in preferences). I would recommend gnome do over deskbar. It has interesting features  and looks better IMO, so you might want to give it a try. 

just do 
```
sudo apt-get install gnome-do
``` in a terminal to install it.

[http://do.davebsd.com/](http://do.davebsd.com/) is the website.

---

### Post by pound_forthesound on 2008-07-18
That's pretty cool, I haven't seen that app before, it doesn't seem to have quite the same functionality though... (unless I'm doing it wrong)

---

### Post by pound_forthesound on 2008-07-19
*bump* any more ideas? :D

Edit: fixed the inactive windows thing!

For reference - in to gconf editor go to /apps/gwd and change metacity_theme_opacity to 1

---

