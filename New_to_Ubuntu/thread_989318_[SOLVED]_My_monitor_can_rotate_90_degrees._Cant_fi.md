---
title: "[SOLVED] My monitor can rotate 90 degrees. Cant find any setings to rotate the deskto"
date: 2008-11-21
forum: New to Ubuntu
---

### Post by philinux on 2008-11-21
This is useful for portrait picture editing etc.

---

### Post by TeoBigusGeekus on 2008-11-21
Would this be of any help?
[http://ubuntuforums.org/showthread.php?t=478244&highlight=rotation+dell]("http://ubuntuforums.org/showthread.php?t=478244&highlight=rotation+dell")

---

### Post by philinux on 2008-11-21
That was bizarre. It works but only by editing xorg.conf, everytime you want it rotated. I'd like to be able to use the rotate within system>prefs>screen res.

Wallpaper looked weird. LOL

---

### Post by philinux on 2008-11-21
Under Rotate I've now got normal or upside down. I'd like CW right to be a choice. Looks like I'll have to do some more digging. Stepping in the right direction though. Upside down is a start. If freaky to reverse.

---

### Post by TeoBigusGeekus on 2008-11-21
Glad to be of any help...
Keep us posted if you finally solve it!

---

### Post by philinux on 2008-11-21
Terminal ha ha.

xrandr -o right
xrandr -o normal
xrandr -o left
xrandr -o invert

If anyone needs this.

Shame the gui cant do it.

---

### Post by steveneddy on 2008-11-21
Just posting so I can find this tonight.

Thanks.

---

### Post by gyaneshwar on 2010-01-20
Just to add more functions:

In case you have more monitors:

Step 1
in terminal type
xrandr -q

Step 2
Try to rotate right (any) screen: (this you will get for the Step 1)

xrandr --output DVI-0 --rotate right

if it works you are done otherwise
you will get mismatch of virtual screen resolution


Step 3

Put above virtual resolution in xorg.conf


Step 4
Restart machine or kill the xdm or whatever you prefer.

Step 5
Now you can change rotation of that screen either from terminal or from Preferences-Display menu

More details you can find in following posts but above is core idea.
[http://ubuntuforums.org/showthread.php?t=1199329](http://ubuntuforums.org/showthread.php?t=1199329)
[http://forums.overclockers.com.au/showthread.php?t=792414](http://forums.overclockers.com.au/showthread.php?t=792414)

---

