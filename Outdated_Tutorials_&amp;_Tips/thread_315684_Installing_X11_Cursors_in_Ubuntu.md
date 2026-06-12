---
title: "Installing X11 Cursors in Ubuntu"
date: 2006-12-09
forum: Outdated Tutorials &amp; Tips
---

### Post by xomnia on 2006-12-09
Just thought I would throw this in here since I looked on google and the forums and it looks like no one has posted how to install these themes, and for me at least, it wasn't self explanatory though not to hard to figure out.

1. Download the theme (I get mine from [http://gnome-look.org](http://gnome-look.org))
2. Extract the folder inside
3. Copy the theme's folder to /usr/share/icons (In order to use file browser for this  u can run it from the terminal as root with:

```
sudo nautilus
```

4. Go to System -> Preferences -> Mouse and select the pointers tab, scroll down and you should find your theme there.

That should do it!

---

### Post by Ferio on 2006-12-11
There's an easier way: just install *gcursor* (in universe repositories)
```
sudo apt-get gcursor
```
and you'll get a GUI to do it.

---

### Post by Redeyes_Gambit on 2007-01-14
Shouldn't that be "sudo apt-get install gcursor" ?

---

### Post by JaNoLeRRo on 2007-01-14
> **Redeyes_Gambit said:**
> Shouldn't that be "sudo apt-get install gcursor" ?
Yes, the correct line is: sudo apt-get install gcursor
or can be: sudo aptitude install gcursor
any line works perfectly

---

### Post by MadnessRed on 2008-10-29
That doesn't work for me :'( I Run the program I see my cursor and select it nothing happens, also the buttons don't do anything install theme doesn't work and neither does the view theme folder, if I click install theme then go into appearances an then select my theme and then go to pointers my cursors aren't there.

Any ideas?

---

### Post by GarrisonM011 on 2009-01-19
how do u run it???
I dont see any icon

---

### Post by [.root/fail] on 2009-04-12
> **MadnessRed said:**
> That doesn't work for me :'( I Run the program I see my cursor and select it nothing happens, also the buttons don't do anything install theme doesn't work and neither does the view theme folder, if I click install theme then go into appearances an then select my theme and then go to pointers my cursors aren't there.

Any ideas?

This exact same thing happened for me. Please help. [BUMP!]

---

### Post by lucidsundivine on 2009-05-30
also having this problem! halp!

---

### Post by BslBryan on 2009-05-30
Why don't you just follow the OP's tutorial?  He never said anything about Gcursor.

---

### Post by BIGtrouble77 on 2009-05-31
gcursor is not a very good program.  All it really does is give you a link to the theme directory.  You can easily change your cursor in the appearance preferences (once it's been copied to ).

One rule of thumb... if a program does not show up in the ubuntu menu then just run it from the command line.  Typing 'gcursor' in a terminal isn't that difficult.

---

### Post by binbash on 2009-06-01
Forget Gcursor, it is a crap software.

---

### Post by Lawngnome on 2009-06-02
I installed a theme but the new cursor is only visable when the cursor is over firefox.  Any other window and in system menu's I still have the old cursor.

---

### Post by Malart on 2009-06-03
> **Lawngnome said:**
> I installed a theme but the new cursor is only visable when the cursor is over firefox.  Any other window and in system menu's I still have the old cursor.


i believe that means you have to restart the X server. so log out and then back in, and that will hopefully fix it.

---

### Post by db. on 2009-06-04
i tried both ways... ofcourse the easy dumping of files, but system>pref>mouse> i dont have a pointer tab, and also n the gcursor stated before, installing theme doesnt work.

---

### Post by Shpongle on 2009-07-21
> **Lawngnome said:**
> I installed a theme but the new cursor is only visable when the cursor is over firefox.  Any other window and in system menu's I still have the old cursor.

same here, are you running compiz? , that seems to be the cause of the problem for me

---

