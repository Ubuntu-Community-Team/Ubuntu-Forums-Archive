---
title: "Configuring Gnome-search-tool?"
date: 2008-05-19
forum: New to Ubuntu
---

### Post by entropism on 2008-05-19
hey folks, probably a REALLY dumb question, but better to ask and learn, right?

I'm trying to get my mouse configured with Hardy, and I have BTNX pretty much set up, but I'm trying to get my middle mouse button to open a new tab in firefox.  Well, I've succeeded in doing that, but every time I hit my middle mouse button, it also opens the gnome-search-tool.  Is there any way I can change how the search tool opens, or better yet disable it completely from opening on a mouse click?

Thanks in advance!

---

### Post by wolfen69 on 2008-05-19
cant directly help you with your problem, but i use a firefox addon called firegestures. if you like mouse gestures, you can configure it to open new tab with any gesture you want. i use right click-down.

---

### Post by entropism on 2008-05-20
Bump, anyone else?

---

### Post by entropism on 2008-05-21
Bumping this off page 7

---

### Post by TomPreuss on 2008-05-21
> **entropism said:**
> hey folks, probably a REALLY dumb question, but better to ask and learn, right?

I'm trying to get my mouse configured with Hardy, and I have BTNX pretty much set up, but I'm trying to get my middle mouse button to open a new tab in firefox.  Well, I've succeeded in doing that, but every time I hit my middle mouse button, it also opens the gnome-search-tool.  Is there any way I can change how the search tool opens, or better yet disable it completely from opening on a mouse click?

Thanks in advance!
I'm having the same exact issue, any help would be appreciated.

(For those finding this thread looking for similar issues, the btnx config thread is here: [http://ubuntuforums.org/showthread.php?p=2727025](http://ubuntuforums.org/showthread.php?p=2727025) (this is what you probably need to get buttons on your mouse to do what you want (middle click properly, etc.))

What we need here is for the middle button to do what we want (middle click) and not (also) the default (open the search tool).

As stated, thanks in advance!

---

### Post by entropism on 2008-05-22
ugh, finally fixed this:

From the BTNX thread:

Anyway try rebinding the Search function using gnome-keybinding-properties, it won't solve the middle_click problem but at least you won't see the search interface every time you press the middle button.

Went into the keybindings and disabled search.  Problem solved.

---

