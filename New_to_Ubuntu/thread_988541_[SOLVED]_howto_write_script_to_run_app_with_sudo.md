---
title: "[SOLVED] howto write script to run app with sudo ?"
date: 2008-11-20
forum: New to Ubuntu
---

### Post by krtica on 2008-11-20
For most of you, this is probably stupid question. :oops:

I have installed LaCie LightScribe Labeler, but when I run it and when I wanna to print, I get message that I have to be root to print.. Something like this.

So, when I type
$ sudo /usr/4L/4L-gui
in terminal, and when I type pass, everything is ok.

Is there any way to write some script and run it under Main Menu, so that I don't need to use terminal? :confused:

PS: I'm OK with terminal, but some of my family members are not. :D I'm fighting for keeping Ubuntu on comps... :D

Thx.

---

### Post by bodhi.zazen on 2008-11-20
Add any users (or a group if you wish) in sudoers to run the command w/o a password.

Keep the short cut "sudo /usr/4L/4L-gui'

keep /usr/4L/4L-gui owned by root. executable by root.

[http://www.gratisoft.us/sudo/man/sudoers.html](http://www.gratisoft.us/sudo/man/sudoers.html)

---

### Post by krtica on 2008-11-20
I already tried with sudo /usr/4L/4L-gui in Launcher, but nothing is happen.
/usr/4L/4L-gui is owned by root and executable by root. I also tried to put user in root group, but it didn't help neither.
I'll try to read first Sudoers Manual before I ask another question. :D

---

### Post by caljohnsmith on 2008-11-20
If you right-click your Applications menu, select "Edit Menus", the you can use the "New Item" button to add an application launcher in one of your menus for your "4L-gui" program. In the "command" field of that launcher, just put:
```
gksudo /usr/4L/4L-gui
```
And I'm assuming that because your app says "gui" at the end, it is truly a GUI app; if that is the case you should be using gksudo and not sudo to run it as shown above. And if you don't want to have to type in a password for it, just follow Bodhi.zazen's advice about adding the app to sudoers. Let us know how it goes. :)

---

### Post by bodhi.zazen on 2008-11-20
oooo, good call on the gksudo, I missed that :redface:

---

### Post by krtica on 2008-11-20
Thx caljohnsmith _o_
It works.

This literature is quite dificult for me, but I already learned that sudores is a file. :D
I'm beginner, but I'm willing to learn. :D

---

### Post by bodhi.zazen on 2008-11-20
> **krtica said:**
> This literature is quite dificult for me, but I already learned that sudores is a file. :D
I'm beginner, but I'm willing to learn. :D

We understand, but it is difficult to know what your knowledge base is from your posts or post count (do not assume high post count = better knowledge).

If you see a response you do not understand, just ask for clarification and you will almost certainly receive it in abundance.

---

### Post by krtica on 2008-11-20
thx. i will. i'm just a little bit ashamed of my emptiness in linux knowledge. :D

---

