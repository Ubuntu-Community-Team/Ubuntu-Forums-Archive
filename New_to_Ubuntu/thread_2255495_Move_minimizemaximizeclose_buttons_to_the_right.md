---
title: "Move minimize/maximize/close buttons to the right"
date: 2014-12-05
forum: New to Ubuntu
---

### Post by Evil Wayz on 2014-12-05
Ok I have gnome tweak tool and it let me change the window, gtk, icon and pointer.  But the controls for the windows are all on the left side, and that annoys me.  How do I get the controls to be on the right?  I'm talking about the minimize/maximize/close buttons.

Using Gnome Flashback session.

---

### Post by buzzingrobot on 2014-12-05
If it's Unity, you can't these days.  Was possible, in earlier releases, but no longer. (Assuming you aren't really running 11.04)

If it's Gnome Shell, the buttons are on the right by default.

---

### Post by vasa1 on 2014-12-05
> **Evil Wayz said:**
> Ok I have gnome tweak tool and it let me change the window, gtk, icon and pointer.  But the controls for the windows are all on the left side, and that annoys me.  How do I get the controls to be on the right?  I'm talking about the minimize/maximize/close buttons.
Use a more customizable desktop environment or window manager. IIRC, the developers of Unity have technical reasons for not allowing the buttons to be moved.

---

### Post by Mark Phelps on 2014-12-05
> How do I get the controls to be on the right? I'm talking about the minimize/maximize/close buttons. 

The comments by buzzingrobot are correct -- you can't change them anymore!  

These used to be easily modified and, you could install Ubuntu Tweak and do it that way, but now, Ubuntu has changed the infrastructure for the window buttons, and they can not be shifted to the right anymore.

Personally, I never liked the buttons on the left, and now you can't change them, after switching between Mint and Ubuntu over the years, I've decided to stay with Mint -- which has all the features of Ubuntu and STILL has the buttons on the right.

---

### Post by Evil Wayz on 2014-12-05
I just migrated from Mint 17 Mate  because I couldn't get Bluetooth to work.  I guess I'll have to deal with buttons on the left.  But I don't have to like it.  :P  I'm using gnome flashback, shouldn't the buttons be on the right?

---

### Post by vasa1 on 2014-12-05
> **Evil Wayz said:**
> ... I'm using gnome flashback, shouldn't the buttons be on the right?
That information would be better off in the first post.

---

### Post by Evil Wayz on 2014-12-05
OK edited and changed my distro.  That should tell you when I left for Mintland.  :)

---

### Post by buzzingrobot on 2014-12-05
I wonder what would happen if someone put the buttons in the middle....?

---

### Post by kccv42 on 2014-12-05
Switching from windows, you kind of get used to the new layout of ubuntu after a while.

---

### Post by Paulgirardin on 2014-12-05
You don't need the buttons in Unity.You can close and minimise/maximise from the launcher and drag the menu bar to maximise/de-maximise

---

### Post by ibjsb4 on 2014-12-05
> **Evil Wayz said:**
> Ok I have gnome tweak tool and it let me change the window, gtk, icon and pointer.  But the controls for the windows are all on the left side, and that annoys me.  How do I get the controls to be on the right?  I'm talking about the minimize/maximize/close buttons.

Using Gnome Flashback session.

In terminal:
```
gsettings set org.gnome.desktop.wm.preferences button-layout :minimize,maximize,close
```
[http://ubuntuforums.org/showthread.php?t=2184682](http://ubuntuforums.org/showthread.php?t=2184682)

Also a 12.04 reference.
[https://help.ubuntu.com/community/PreciseGnomeClassicTweaks#Move_Minimize.2BAC8-Maximize.2BAC8-Close_Buttons](https://help.ubuntu.com/community/PreciseGnomeClassicTweaks#Move_Minimize.2BAC8-Maximize.2BAC8-Close_Buttons)

---

### Post by vasa1 on 2014-12-05
> **Paulgirardin said:**
> You don't need the buttons in Unity.You can close and minimise/maximise from the launcher and drag the menu bar to maximise/de-maximise
I'm not sure they're needed in any distro. Alt+Spacebar followed by N or C or X does it just fine.

---

### Post by kccv42 on 2014-12-05
Paulgirardin got a good point.

---

### Post by pfeiffep on 2014-12-06
> **Evil Wayz said:**
> Ok I have gnome tweak tool and it let me change the window, gtk, icon and pointer.  But the controls for the windows are all on the left side, and that annoys me.  How do I get the controls to be on the right?  I'm talking about the minimize/maximize/close buttons.

Using Gnome Flashback session.I used this[ link]("http://askubuntu.com/questions/9867/how-to-switch-window-controls-to-the-left-gnome-shell") and found that moving the windows control to the right is possible **IF** one uses desktop environment Gnome-Session-Flashback

Enter a terminal session by using Ctrl-Alt-t then execute this line of code

```
gsettings set org.gnome.desktop.wm.preferences button-layout ':minimize,maximize,close'
```

---

### Post by Mark Phelps on 2014-12-06
From what I've read, those changes don't work anymore.  They did with older versons of Ubuntu, but not with the current one and the Unity desktop.

---

### Post by pfeiffep on 2014-12-06
> **Mark Phelps said:**
> From what I've read, those changes don't work anymore.  They did with older versons of Ubuntu, but not with the current one and the Unity desktop.OP is not using Unity but rather Using Gnome Flashback session.

---

### Post by edwardsah3 on 2015-01-29
I just found this thread in ask ubuntu that solves it completely

[http://askubuntu.com/questions/174292/how-can-i-move-all-the-window-controls-to-the-right-or-left](http://askubuntu.com/questions/174292/how-can-i-move-all-the-window-controls-to-the-right-or-left)

The crux is the following command.

gsettings set org.gnome.desktop.wm.preferences button-layout ':minimize,maximize,close'

---

