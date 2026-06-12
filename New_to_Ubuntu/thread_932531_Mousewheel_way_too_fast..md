---
title: "Mousewheel way too fast."
date: 2008-09-28
forum: New to Ubuntu
---

### Post by Preturbed on 2008-09-28
I just installed Ubuntu and I'm really enjoying it, except for this little minor detail. I have a Microsoft (hey that could be the problem!) Wireless Laser Mouse 6000. Whenever I use the mousewheel, it scrolls WAY too fast this isn't a problem with FF, it's the same through the whole os. I can't shortcut to "that other desktop" by scrolling because the slightest movement causes something like 4 "button presses." 

I tried a different mouse and realized the wheel on the mouse in question has a smooth motion (no clicks) and I imagine thats the problem. Now how do I fixes it?

---

### Post by Preturbed on 2008-09-29
Any help would be much appreciated.

Also the sound output seems a little quiet.

---

### Post by unutbu on 2008-09-29
Regarding mousewheel speed:
[http://ubuntuforums.org/showpost.php?p=3951507&postcount=6](http://ubuntuforums.org/showpost.php?p=3951507&postcount=6)

The solution posted there seems to work for some, but not all machines.

Regarding volume:
Have you tried the volume control applet (Right-click on the gnome panel, select "Add to Panel", Select the "Volume Control" applet).

If you are using ALSA, you might also want to try opening a terminal and typing
```

alsamixer
```

This will open a terminal program. By using the arrow keys you can control the volume of various sound output channels your sound card might support.

---

