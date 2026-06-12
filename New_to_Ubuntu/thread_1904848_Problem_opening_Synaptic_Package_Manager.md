---
title: "Problem opening Synaptic Package Manager"
date: 2012-01-05
forum: New to Ubuntu
---

### Post by tkabir11 on 2012-01-05
So I just installed Synaptics Package Manager through the software center on Ubuntu 11.10. When I try opening synaptics from the dash- it asks me for my password- I enter my password- and thats it...nothing happens :/ But when I try to open it from terminal- it opens just fine- but I get this one warning message several times on the terminal: 

(gksudo:2407): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

Any idea what does this mean? And does anyone know how I could open synaptics without using the terminal? 
Thanks

---

### Post by anewguy on 2012-01-05
Well, this is going to sound like it shouldn't apply, and that's what I thought when I first read it, but I had this same problem and the fix works, it's just strange:

open up the settings, then accessability.

turn on, then turn off the on screen keyboard

turn on, then turn off the voice reader

reboot

I know it's strange, but I found that in the forum and it fixed it for me.

Also, don't worry about the pixmap error messages.

Dave ;)

---

### Post by tkabir11 on 2012-01-05
> **anewguy said:**
> Well, this is going to sound like it shouldn't apply, and that's what I thought when I first read it, but I had this same problem and the fix works, it's just strange:

open up the settings, then accessability.

turn on, then turn off the on screen keyboard

turn on, then turn off the voice reader

reboot

I know it's strange, but I found that in the forum and it fixed it for me.

Also, don't worry about the pixmap error messages.

Dave ;)


Sorry Dave- it didn't work for me :( although I did believe that the simplest problem would often have the weirdest solution :p

---

### Post by cortman on 2012-01-05
> **anewguy said:**
> Well, this is going to sound like it shouldn't apply, and that's what I thought when I first read it, but I had this same problem and the fix works, it's just strange:

open up the settings, then accessability.

turn on, then turn off the on screen keyboard

turn on, then turn off the voice reader

reboot

I know it's strange, but I found that in the forum and it fixed it for me.

Also, don't worry about the pixmap error messages.

Dave ;)

I was having the same problem with my VBox installation of 11.10... but the above procedure didn't fix it...

---

### Post by tkabir11 on 2012-01-06
Mind you- i just installed kubuntu desktop and I don't have any problems opening synaptic on kubuntu.

---

### Post by anewguy on 2012-01-06
I'll see if I can track down the site I got that information from, in case there were other suggestions as well.  I believe this only applied to ubuntu using the Unity interface, but not positive.  I don't think KDE, LDE, etc., would probably have the problem.

Dave ;)

---

### Post by anewguy on 2012-01-06
Okay, found the link via my old thread.  Thanks to Oldos2er (sp??) for the link:

[https://bugs.launchpad.net/ubuntu/+source/synaptic/+bug/839219]("https://bugs.launchpad.net/ubuntu/+source/synaptic/+bug/839219")

These problems are just gnome related.

There are several things to try in that link.  I forgot I removed Orca first, then did the keyboard and sound things.  That worked for me.  You may also need to do the kill of the accessability demon as noted in the first part of the bug report.  This time around I didn't read the report since my problem is fixed, but it is possible someone has added things to the end of the thread which may be of use to you.

Dave ;)

---

