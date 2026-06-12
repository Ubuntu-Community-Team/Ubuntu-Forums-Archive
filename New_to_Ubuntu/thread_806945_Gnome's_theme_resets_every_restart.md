---
title: "Gnome's theme resets every restart"
date: 2008-05-25
forum: New to Ubuntu
---

### Post by corwinspyre on 2008-05-25
Hi!  Every time I restart my X server (normally via ctrl-alt-backspace or a reboot), my theme goes away.  I'm using the "Darklooks" theme, and the only additional themes I have installed are from the package gnome-themes-extras.  When I go to system->preferences->appearance, Darklooks is highlighted as if enabled, but everything is colored like the default theme.  To enable Darklooks again, I have to click on a different theme and then back onto Darklooks.  Further, if I do this without having nautilus open, the default theme will still be applied to it (the same goes for liferea, the rss reader).  

Does anyone know what could be wrong?  Thank you very much, because this is an annoying problem

edit:  In case it matters, I'm running compiz-fusion with emerald on Hardy.

---

### Post by sayakb on 2008-05-25
If you are using emerald, how come you are applying a GTK theme? Maybe you should try removing emerald if you just use the gtk themes. See if that helps. Also, have you kept your session saved? If yes, delete saved sessions from ~/.nautilus folder

---

### Post by corwinspyre on 2008-05-25
Isn't emerald only responsible for window borders?  I use Darklooks to color everything black/dark, not for window borders.  Also, I don't have it set to save/restore my session

---

### Post by sayakb on 2008-05-25
No, Window decorator can either be provided by emerald or the gtk window decorator. If you have emerald installed and running, you might not be able to use GTK window decorators at all (though other components like buttons and menus work well). As you are using a GTK theme, you might not have emerald running. Emerald has it's own set of stunning themes! Get them from gnome-look.org
To switch to emerald, press Alt+F2 and type:
```
emerald --replace &
```

---

### Post by corwinspyre on 2008-05-25
I appreciate the help of course, but I think you're incorrect.  Emerald replaces the GTK window decorator, not metacity, which is what controls the window theme (besides borders).  To make sure, I just tried installing a new emerald theme ([http://www.compiz-themes.org/content/show.php/Ninjja-Dark?content=63196](http://www.compiz-themes.org/content/show.php/Ninjja-Dark?content=63196)), and it only changed the window borders.  I do have emerald running (in ccsm->window decoration->command, I have "emerald --replace", and the compiz-icon shows emerald enabled), and alt-f2 emerald --replace doesn't change anything (that is, it doesn't make Darklooks go away), which makes me think that's not the problem.

---

### Post by sayakb on 2008-05-25
When did I say that emerald replaces metacity (please re-read post #4) ;)
Compiz and Metacity are Window Managers while Emerald and GTK are window decorators..
Plus, if emerald is enabled, you can NOT use the gtk window borders. So if you are getting the GTK window borders (which I predict from the fact that you change your borders from System->Preferences->Appearance), it means that you are using GTK and NOT emerald.. :)

---

### Post by sayakb on 2008-05-25
Just a second, does the darklooks just change the Window controls (eg: Buttons, menus etc) and you have a different window border (other than the GTK darklooks)?? If so, then you might have emerald running  (sorry, I misunderstood). Anyway, emerald would not change the window control anyhow, but only the window borders..

EDIT: Try this: Extract the Darklooks tarball. Open nautilus as root:
```
gksudo nautilus
```
Then copy the darklooks folder to /usr/share/themes.

---

### Post by corwinspyre on 2008-05-25
Yeah, I saw you said that, but was trying to show how we're on different pages.  I wasn't very clear, so let me try a different way:  I do not want different window borders.  I use Darklooks to change the look of the window itself, not to change the look of the window borders.  

I have compiz running instead of metacity, and emerald running instead of the GTK window decorator, and system->preferences->appearance->theme (i.e. Darklooks, in my case) controls the color of the window, not the borders.  I can change the theme without disabling emerald, in fact without emerald changing at all; they are separate.


edit: just saw your newer post and am trying it now

---

### Post by sayakb on 2008-05-25
> **corwinspyre said:**
>   I can change the theme without disabling emerald, in fact without emerald changing at all; they are separate.

Ofcourse you can, if the "theme" word indicates the buttons, windows and menu colors. :)

---

### Post by corwinspyre on 2008-05-25
Well, since I installed it via gnome-themes-extras, I didn't have the tarball, so I googled "darklooks gnome theme" to try to find it, and up came a thread in this forum with someone with the second part of my problem (that not having nautilus open would not apply Darklooks to it, but the poster didn't have the problem of having to re-enable it every X-server restart), and the consensus there is that the theme itself is broken, and "Cillop" is going to replace "Darklooks" soon.  I only have the problem with Darklooks, so I guess that's the problem.  

I apologize for sort of wasting your time.  I searched the forum for stuff like theme not staying, reboot theme, etc., but nothing came up.  I guess I should have searched for darklooks specifically, but didn't realize the problem was in a single theme out of all of them in the gnome-themes-extras package :(

Thank you very much for the help however, because I wouldn't have figured it out otherwise.

---

### Post by sayakb on 2008-05-25
No problems :)

---

