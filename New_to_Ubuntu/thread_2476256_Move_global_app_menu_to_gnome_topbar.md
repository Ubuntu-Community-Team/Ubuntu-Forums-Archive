---
title: "Move global app menu to gnome topbar"
date: 2022-06-21
forum: New to Ubuntu
---

### Post by zmih on 2022-06-21
Hello,

I would like to move my global app menu to gnome's topbar just like macOS does. Is that possible?


Thanks.

---

### Post by vanadium on 2022-06-21
Not really in the standard desktop. There are attempts to achieve this, but in Linux, it is complicated because different apps are programmed using different toolkits, so what works for a GTK3 application won´t work for a Qt application, for example. Add to that that GTK applications actually move away from a traditional menu bar.

Unity desktop went a far way in this, and actually that technology has been adopted in the Mate desktop. So if you really want this, you could switch to Mate (or even Unity).

---

### Post by Dennis N on 2022-06-21
What do you mean by 'global app menu'? Please clarify. All application menus are gnome-shell extensions, and they always install to the top bar.

---

### Post by #&amp;thj^% on 2022-06-21
> **Dennis N said:**
> What do you mean by 'global app menu'? Please clarify.
I'm confused as well???
Do you mean moving the icon that opens the application dashboard to the top of the panel? If so try this:
```
gsettings set org.gnome.shell.extensions.dash-to-dock show-apps-at-top true

```

---

### Post by vanadium on 2022-06-22
"Global menu" means that the application menu bar is not located in the application window, but is always found, for the application in focus, on the same location in the top bar. That is the way it works in Apple OSX, and Ubuntu has implemented this in the Unity desktop, although there, the menu only became visible when hovering the topbar with the mouse.

---

