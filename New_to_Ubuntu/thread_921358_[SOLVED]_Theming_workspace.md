---
title: "[SOLVED] Theming workspace"
date: 2008-09-16
forum: New to Ubuntu
---

### Post by tradet on 2008-09-16
I want to change the appearance of my workspace, the small windows white/brown thing.

How shall I do that?

---

### Post by nothingspecial on 2008-09-16
Right click on your desktop, click change desktop background, click the themes tab and choose another.

However these themes are pretty......., well I don`t wanna be rude.

So have a look here

[http://www.gnome-look.org/](http://www.gnome-look.org/)

---

### Post by Mornedhel on 2008-09-16
A few themes are also available in the repositories.

---

### Post by northern lights on 2008-09-16
I think the OP just wants to alter the Workspace Switcher applet. There's no option for that.

---

### Post by halitech on 2008-09-16
> **northern lights said:**
> I think the OP just wants to alter the Workspace Switcher applet. There's no option for that.

if the OP themes the taskbars as well it should affect the workspace switcher. Mine is currently blueish-grey to match the rest of my desktop.

---

### Post by northern lights on 2008-09-16
Really? Sorted then.

I don't use the applet, was under the impression it'd be unaffected.

---

### Post by halitech on 2008-09-16
I've also changed the opacity of the task bars and the switcher seems to be changed as well. I think as long as the theme supports everything then it will (should) be affected.

---

### Post by tradet on 2008-09-16
I'm using emerald to change the windows theme, currently I have the theme 'Slickness'. It's the window switcher applet I want to configure but currently it's not changed.

A new problem when I restarted my pc: the window border went back to the default brown and I had to type
```
emerald --replace
```
In the run application (alt + f2) to get it back. How do I do so I don't have to do that at startup?

---

### Post by northern lights on 2008-09-16
> **tradet said:**
> It's the window switcher applet I want to configure but currently it's not changed.
Figured. I'm sure halitech can elucidate.

> **tradet said:**
> A new problem when I restarted my pc: the window border went back to the default brown and I had to type
```
emerald --replace
```
In the run application (alt + f2) to get it back. How do I do so I don't have to do that at startup?
Navigate to "System > Preferences > Sessions" and add 'emerald --replace' under the "Startup Programs" tab.

---

### Post by halitech on 2008-09-16
maybe I got lucky and its not supposed to work but I'm not using compiz or emerald either so maybe thats the difference

---

### Post by Mornedhel on 2008-09-16
I use Compiz, and the workspace manager does comply to the theme settings. I think it also did while I was on Dapper Drake without Compiz.

---

### Post by tradet on 2008-09-16
Hm I found the other themes changing it.. maybe it's the theme that doesn't support it.

Edit: Found the settings in customize theme->colors. Should be fine

---

### Post by northern lights on 2008-09-16
> **halitech said:**
> maybe I got lucky and its not supposed to work but I'm not using compiz or emerald either so maybe thats the difference
I meant to say "I figured it was the workspace switcher applet the OP was after", not "I figured it can't be changed". If it works for you, I'm pretty certain that on that aspect, I was mistaken.

I think the OP simply hasn't added any particular gtk panel theme. Maybe just point him/her to yours.

Neither compiz nor emerald affect the panel(s). Even if you use compiz for visual effects and emerald for a window decorator, colors, pointers, icons and buttons are still handled as they were before (System > Preferences > Appearance > Customize Button).

---

