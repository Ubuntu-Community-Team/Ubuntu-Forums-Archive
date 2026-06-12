---
title: "[SOLVED] Some noob questions"
date: 2008-06-06
forum: New to Ubuntu
---

### Post by rudedoggx on 2008-06-06
Hey guys, I just started using a full install of Ubuntu 8.04 4 days ago, but I seem to be having some strange and annoying problems: 

I have 2 'Desktop' links in the top section of Places.

When running a game in WINE, my wallpaper will flicker behind the game every 2-3 seconds. While the games are still playable, this is very annoying.

As of last night, my PC randomly began booting into low-graphic mode.

Sometimes the top of my window will 'snap' under the main panel at the top, and I cannot control the window anymore (I'm a noob).

Also, when watching videos in VLC, the videos seem to have a tiny bit of graphical lag, especially when watching in fullscreen.

One more thing: I dragged 'Desktop' to my desktop by accident, now I can't delete it!

Thanks in advance, I guess, and I don't know if I should post anything more to help you out?

---

### Post by Joeb454 on 2008-06-06
Go to System > Preferences > Appearance

And turn off desktop effects (I believe you have Compiz enabled) this could solve some of your issues :)

---

### Post by sayakb on 2008-06-06
*Removing Desktop from places:*
Open any nautilus window and goto Bookmarks->Edit and remove any redundant Desktop entry.

[I]WINE problem:
[/I]Seems like OpenGL problem. Before you play the game, open a terminal and type:
```
metacity --replace &
```
And after you quit the game:
```
compiz --replace &
```

[I]Window snapping:
[/I]Try pulling it down by dragging it by pressing Alt and clicking anywhere on the Window

[I]VLC problem:
[/I]Goto Settings->Preferences
**Check** the Advanced Options checkbox @ bottom right
Now expand Video in left panel and select Output modules
Change output module to X11 video output

---

### Post by rudedoggx on 2008-06-06
Well, desktop effects are already off, due to my system being in 'low-graphic mode'.

What is Nautilus?

---

### Post by hyper_ch on 2008-06-06
(1) use a descriptive thread title and not a generic "noob here" or "help needed"

(2) questions to unrelated problems are better splitted up and answered individually

---

### Post by sayakb on 2008-06-06
Nautilus is Gnome's default file manager. Open your home folder for instance and then goto Bookmarks->Edit

---

### Post by rudedoggx on 2008-06-06
thanks for the forum etiquette (?) hyper_ch. I thought it'd be easier if my problems were addressed all at once.

---

### Post by hyper_ch on 2008-06-06
nope, if the problems/questions are unrelated and only a few are answered or not, it is a lot harder to see where still is a problem.

However if you have individual threads and something got answered, you can mark the thread as solved.

P.S.: And creating several threads with the individual things also raises your post count ;)

---

### Post by rudedoggx on 2008-06-06
Well, thanks guys.. 3/5 solved!

---

