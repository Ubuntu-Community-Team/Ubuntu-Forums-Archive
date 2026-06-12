---
title: "Adding a command to menu using terminal"
date: 2009-06-11
forum: Packaging and Compiling Programs
---

### Post by lexen on 2009-06-11
Hey everybody, I am wondering if it is possible to add a command to the applications menu using terminal.  More specifically, I would like to add the command
```
'/usr/local/games/fofix/FretsOnFire'
```
as an application in the Games sub menu.  I am doing this because I am trying to make a .sh file to download and install a game called fofix.  It's based on the instructions to download and install from source, but they didn't explain how to run the program and they didn't add it to the menu, so I thought I would try to help out.  I have attached what I have done so far with the .sh.


Thanks,
Lexen

---

### Post by pmlxuser on 2009-06-11
why not just use the simpliest GUI way
goto:

> system >Preferences > main menu > games > new item >browse to the program or add the command..

viola

---

### Post by lexen on 2009-06-11
I would, but I am trying to get it to happen within the terminal because I am going to put it in a .sh file.  The end result should be a .sh file that will download the program, install it and add it to the menu, so from the users viewpoint, it would be almost as good as a .deb file, which I am unable to make.

   Thanks for the input.

---

### Post by Linteg on 2009-06-11
Create a .desktop file and install it with deskop-file-install yourapp.desktop. Take a look in /usr/share/applications/ if you want to see how .desktop files look.

Why are you unable to make a deb?

---

### Post by jyaan on 2009-06-11
.desktop files are probably the best way. You can easily set the category, icon, etc.

I also suggest using .deb instead. .deb files are actually very easy to make, and once you learn how it's not a problem and you'll wonder why you waited so long to figure it out.

---

### Post by lexen on 2009-06-11
Thanks everybody.  You have been a big help!  I think I am going to go with a .desktop file for now.  I simply can't figure out how to make .deb files, but if there is a simple and complete tutorial somewhere, I would love to learn.

---

### Post by jyaan on 2009-06-12
There are a few good ones out there. I learned it from the Debian documentation, and I felt it was well written and easy to follow.

I recently saw a sticky in the programming section of the forums here, although I haven't actually read through it.

---

### Post by Moyamo on 2010-08-28
[http://tommed.tumblr.com/post/84365710/how-to-programmatically-create-gnome-start-menu-items](http://tommed.tumblr.com/post/84365710/how-to-programmatically-create-gnome-start-menu-items)

the tutorial

---

