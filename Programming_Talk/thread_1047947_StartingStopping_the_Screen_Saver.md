---
title: "Starting/Stopping the Screen Saver"
date: 2009-01-22
forum: Programming Talk
---

### Post by HyperHacker on 2009-01-22
I'm not using XScreenSaver; just the "Screen Saver" in the settings manager. I want to programmatically start and stop the screen saver, but each one is its own process, so I'd have to know which process to kill/start. How can I do this? Is it safe to just "killall foo" if I know which process it is, or is there a better way?

(I of course can just install XScreenSaver, but I want it to work on systems that aren't using it too.)

---

### Post by twisted_steel on 2009-01-22
It looks like the 'proper' way to do this is to interact with the screensaver over D-Bus. There are some examples on this page: [http://www.gnome.org/~mccann/gnome-screensaver/docs/gnome-screensaver.html#gs-examples]("http://www.gnome.org/%7Emccann/gnome-screensaver/docs/gnome-screensaver.html#gs-examples"). I also found another page that suggested looking at Totem's source code for screensaver interaction: [http://svn.gnome.org/viewvc/totem/trunk/lib//totem-scrsaver.c?view=markup](http://svn.gnome.org/viewvc/totem/trunk/lib//totem-scrsaver.c?view=markup). I believe this is used in Totem to temporarily disable the screensaver while you are watching a movie.

---

Hmm, unless I misread your post and you just want to spawn new gnome-screensaver processes, each with a different screensaver. If that's the case, please ignore the beginning of my post :P

---

### Post by HyperHacker on 2009-01-23
Spawn them and terminate them. Your mention of gnome-screensaver led me to gnome-screensaver-command, which has the --activate and --exit options. That's what I needed. Thanks.

---

### Post by twisted_steel on 2009-01-24
Great to hear. Good luck with your program.

---

