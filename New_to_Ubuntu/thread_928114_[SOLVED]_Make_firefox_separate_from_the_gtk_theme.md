---
title: "[SOLVED] Make firefox separate from the gtk theme?"
date: 2008-09-23
forum: New to Ubuntu
---

### Post by kamitsukai on 2008-09-23
When I have a dark coloured gtk theme in ubuntu it changes the colour of the Firefox toolbar and also search boxes/forms in Firefox...:mad: is there anyway to stop this from happening?

Thanks in advance!

---

### Post by jimmy the saint on 2008-09-23
I kind of doubt it.  You may try installing some firefox theme addons from their site as that may override the default behavior.  The window manager is responsible for drawing the windows and uless specifically told otherwise, simply uses the default theme.  Its an interesting questions.  Be sure to post back here and let us know how well that works.

---

### Post by jimmy the saint on 2008-09-23
Interesting question.  You could try installing one of the firefox themes from the mozilla addons site.  That may override the window manager's default behavior of relying on the theme.  If you try it, be sure to let us know how it worked and mark this thread as solved.

Sorry about the double post, for some reason it took my first 5 minutes to show up!

---

### Post by SunnyRabbiera on 2008-09-23
well if you change the theme it can do this, some themes on the mozilla theme site does override the default theme

---

### Post by I wanted to leave on 2008-09-23
Type in **about:config** into the search box and hit enter, accept the warning and scroll down to 
**browser-use-system-colors** whatever, double click and the option will change to false

If that doesn't work, you can also change search bar background and text colors individually

---

### Post by nufros on 2008-11-13
You could also try this Greasemonkey script... it worked for me :)

[http://userscripts.org/scripts/show/36850]("http://userscripts.org/scripts/show/36850")

---

