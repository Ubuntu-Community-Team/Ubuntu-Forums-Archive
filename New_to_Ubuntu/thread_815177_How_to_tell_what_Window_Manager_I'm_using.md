---
title: "How to tell what Window Manager I'm using?"
date: 2008-06-01
forum: New to Ubuntu
---

### Post by WBL on 2008-06-01
I know that I'm running Compiz, but I have no idea what Window Manager I'm using!

I'd like to know so that I can get some themes.

-WBL

---

### Post by shifty_powers on 2008-06-01
what version of ubuntu?

ubuntu = gnome
kubuntu = kde
xubuntu = xfce

and so on...

---

### Post by lizzard on 2008-06-01
Fire up gnome-system-monitor (->System ->Administration -> gnome-system-monitor) and look for processes called either metacity or emerald. (I think these are the only usual possibilities.) That's the window-manager which is running on your system.

---

### Post by FuturePilot on 2008-06-01
If you're using Compiz you're either using the gtk-window-decorator or Emerald. By default the gtk-window-decorator is used unless you install Emerald. Then Emerald gets used.

---

### Post by Joeb454 on 2008-06-01
If you have a normal Ubuntu install - the default WM is Metacity, though I'm sure this changes with Compiz, as FuturePilot mentioned above :)

---

### Post by WBL on 2008-06-01
It turns out that I'm using gtk-window-decorator.

Can I install Emerald (for the themes) without it messing up my Compiz?

-WBL

---

### Post by Gamma746 on 2008-06-01
Compiz is a window manager.  It replaces your desktop environment's default window manager. (usually Metacity or KWin)

Gnome/KDE/XFCE are desktop environments; gtk-window-decorator/Emerald are window decorators.

---

### Post by WBL on 2008-06-01
> **Gamma746 said:**
> Compiz is a window manager.  It replaces your desktop environment's default window manager. (usually Metacity or KWin)

Gnome/KDE/XFCE are desktop environments; gtk-window-decorator/Emerald are window decorators.

What I'm asking is this - can I replace gtk-window-decorator with Emerald, or would that possibly mess up my Compiz?

-WBL

---

### Post by WBL on 2008-06-01
OK, I installed Emerald, but it's not running!  gtk-window-decorator is still running.  How do I switch back and forth?

-WBL

---

### Post by markbuntu on 2008-06-01
If you don't have the compiz fusion icon you should get it. Then you can change your window decorators by right clicking on it and looking at the choices. Also, you need to restart x to get it to work, ctrl alt backspace is the fast way.

---

### Post by cypry_radu on 2009-07-19
I think the best way is to install **wmctrl**.

> sudo apt-get install wmctrl

then open a terminal and type:

> wmctrl -m

In my case I get:

[B]Name: Metacity
Class: N/A
PID: N/A[/B]

I know maybe is quite late response for you but for other users might be useful.

---

### Post by michael.g.sheldon on 2012-09-06
Here's a way to determine your window manager that doesn't rely on you already knowing the name of the window manager binary:

```
update-alternatives --get-selections | grep x-window-manager
```

Cheers!

---

### Post by sisco311 on 2012-09-06
[[img]http://ompldr.org/tYzBtcQ[/img]](http://ompldr.org/vYzBtcQ)

---

