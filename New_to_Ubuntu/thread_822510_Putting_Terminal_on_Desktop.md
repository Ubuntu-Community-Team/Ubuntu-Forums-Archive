---
title: "Putting Terminal on Desktop"
date: 2008-06-08
forum: New to Ubuntu
---

### Post by idolguy on 2008-06-08
Hey, I've installed Ubuntu successfully!  I would like to be able to put a "link" to the terminal on the desktop.  That way I would not have to go to Applications/Accessories/Terminal every time I want to type in a command.  Can I create a shortcut on the desktop to the Terminal?

Thanks!

---

### Post by Barriehie on 2008-06-08
Yes you can.  When you get to the terminal via the menus simply right click and you should have the option of adding it to the desktop.  I've got mine setup that way and then if you add --geometry=124x13 (substituing your columns and rows) you can have it open up at the display size you desire.  This can be globally set in your .bashrc or kept local for that launcher by editing the properties.

So. your launcher command could look like this:
```
gnome-terminal --geometry=124x13
```Barrie

---

### Post by drs305 on 2008-06-08
The command is "gnome-terminal". I put a shortcut on my top panel.

---

### Post by cprofitt on 2008-06-08
Yes...

steps:

right click on desktop
select create launcher

in the pop-up:

Name:  Terminal
Command: gnome-terminal
Comment: none

click ok

Personally I like to put such links on the top panel though so they are easily accessible when I have other apps open already.

That is even easier...

steps:

right click top panel
select add to panel
select application launcher (this copies an existing one)
toggle the accessories category open
select Terminal and click +Add

Hope this helps.

---

### Post by Sealbhach on 2008-06-08
You can just drag it from the menu to the desktop. Also drag it onto the top or bottom panels if you like.


.

---

### Post by idolguy on 2008-06-08
> **PrivateVoid said:**
> Yes...

steps:

right click on desktop
select create launcher

in the pop-up:

Name:  Terminal
Command: gnome-terminal
Comment: none

click ok

Personally I like to put such links on the top panel though so they are easily accessible when I have other apps open already.

That is even easier...

steps:

right click top panel
select add to panel
select application launcher (this copies an existing one)
toggle the accessories category open
select Terminal and click +Add

Hope this helps.

=======================================================================
Yes, this helped quite a lot.  Thanks to you (and to all who replied)!

---

### Post by cprofitt on 2008-06-08
You are welcome; Ubuntu has a fantastic community that you will find willing to help you as your continue using Ubuntu.

---

