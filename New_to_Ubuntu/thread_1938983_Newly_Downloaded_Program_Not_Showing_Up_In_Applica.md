---
title: "Newly Downloaded Program Not Showing Up In Application Menu"
date: 2012-03-10
forum: New to Ubuntu
---

### Post by KelinciHutan on 2012-03-10
I recently downloaded a game called enigma through the Software Center.  And after it downloaded, I went to go play it and found that it wasn't in the games menu anywhere.  After double-checking that the Software Center was indeed reporting the program as installed, I checked through the rest of the Applications menu to see if it had been misplaced, but no luck.  I tried using the file finder to see if I could at least identify where the folder had gone, but that didn't turn anything up either.  Nor could I locate it using Ubuntu tweak.  Opening Nautilus and showing the hidden folders in home didn't seem to do any good either.

So, at this point, I was fairly bewildered, and so I uninstalled it from the Software Center and reinstalled using the terminal.  With identical results.  The Software Center says the program is installed, but I can't find the actual program anywhere. :confused:

Erm...and I am running Lucid.

---

### Post by winh8r on 2012-03-10
The game will be in /usr/games

you could also launch it from the terminal by entering

```
enigma
```

hope this helps you

---

### Post by KelinciHutan on 2012-03-10
That found it.  Thanks!

I am curious, though.  Is there a way I can put it on the menu?

---

### Post by winh8r on 2012-03-10
If you right click on Applications

select "edit menus"

you can add it to the menu in there.

I have just tried to enable it but had to use the "New Item" function and enter the name and the command enigma to launch the application, but it all works now in my menu.

Must have a little glitch somewhere that stops it showing up on the menu by default..........something of an enigma I suppose!!!!

---

### Post by KelinciHutan on 2012-03-10
Brilliant!  It worked like a charm.  Thanks so much for the help. :D

---

