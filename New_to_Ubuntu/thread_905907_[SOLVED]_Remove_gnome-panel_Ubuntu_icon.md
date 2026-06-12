---
title: "[SOLVED] Remove gnome-panel Ubuntu icon"
date: 2008-08-30
forum: New to Ubuntu
---

### Post by BlueMendicant on 2008-08-30
Hi,

I was curious if there was a way to replace the default Ubuntu icon in gnome-panel to the gnome foot rather than the Ubuntu logo? I searched the forums and there was some information about removing start-here.png and distributor-logo.png from /usr/share/icons/$THEME$ but I tried that with the Human theme (followed by killall gnome-panel) but no luck.

Any help?

Thanks,
BM

---

### Post by spiderbatdad on 2008-08-30
this thread offer two options: [http://ubuntuforums.org/showthread.php?t=167658](http://ubuntuforums.org/showthread.php?t=167658)

---

### Post by drs305 on 2008-08-30
Edited: Complete solution in post #5

If you are looking for the "Main Menu" icon, on my Hardy setup it is /usr/share/icons/Human/24x24/places/start-here.png
This may be very different on each person's setup. When I use gimp to edit the above icon the changes are reflected on the panel after I refresh the Desktop.

If you already know the name and location of the icon you are looking for, make sure it's 24/x24, make a backup of the original and copy the new icon to the location/name above.

Then refresh the deskop with "killall gnome-panel" and see if it replaced it.

---

### Post by spiderbatdad on 2008-08-30
awesome, drs305 worked like a charm.
quickly and easily changed the ubuntu logo to this heart:

---

### Post by drs305 on 2008-08-30
I am using the default (Human) theme in Hardy. I found and used one of the gnome footprint icons in /usr/share/pixmaps. It isn't a 24x24 icon like the original one on my panel but seems to work. If you wish you can resize it using gimp or another graphics program to 24x24.

This will replace the main menu ubuntu logo commonly found on the top panel with the old black gnome footprint. You can use any icon you wish. Just subtitute the location/icon_name in bold with your choice:

Backup original ubuntu main menu icon:
```

sudo cp /usr/share/icons/Human/24x24/places/start-here.png /usr/share/icons/Human/24x24/places/start-here.png.bak

```
Copy/rename gnome footprint icon to replace the ubuntu main menu icon:
```

sudo cp **/usr/share/pixmaps/gnome-about-logo.png** /usr/share/icons/Human/24x24/places/start-here.png

```

Refresh the desktop:
```
killall gnome-panel
```

Enjoy!

---

### Post by BlueMendicant on 2008-08-31
Hi,

Thank you for all your help. I had to resize the gnome-about-logo.png to 24x24 because gnome did not scale for it for me (instead my gnome-panel was huge.) I also had to run "sudo gtk-update-icon-cache /usr/share/icons/Human" to update the icon cache. Not sure why I had to update the icon cache but others did not.

Summary to change Gnome panel icon in Hardy:
```
sudo cp /usr/share/icons/Human/24x24/places/start-here.png /usr/share/icons/Human/24x24/places/start-here.png.bak
sudo cp ***/home/user/24x24.png*** /usr/share/icons/Human/24x24/places/start-here.png
sudo gtk-update-icon-cache /usr/share/icons/Human
killall gnome-panel
```

Thanks!
BM

---

### Post by Badoxide on 2008-08-31
Hello.All

@ drs305

Wow I've been looking, for a way to do this I happen to stop by to see what you had posted, and I just wanted to say thanks it worked I now have that foot. ;)

Have a safe weekend all of you.

Thank you

B-O

---

### Post by cogitordi on 2008-09-10
Is there a configurable/reversible way to remove all the icons from the main menu?

---

### Post by Dipper on 2009-02-10
I tried everything in this thread and the foot is not there. That ubuntu logo is stubbornly showing despite the fact that it no longer exists in any of the /usr/icons directories. I am using intrepid.  Are there any special instructions?

---

### Post by drs305 on 2009-02-11
> **Dipper said:**
> I tried everything in this thread and the foot is not there. That ubuntu logo is stubbornly showing despite the fact that it no longer exists in any of the /usr/icons directories. I am using intrepid.  Are there any special instructions?

Dipper,

I am using 64-bit intrepid and the human (default) theme. I just ran it for intrepid and got these results:
Main menu icon (ubuntu symbol) = /usr/share/icons/Human/24x24/places/start-here.png
Foot icon = /usr/share/pixmaps/gnome-about-logo.png
...
I renamed the start-here.png file in ...24x24 to start-here.png.original
I copied the gnome-about-logo.png to the ...Human/24x24/places folder.
I renamed it to start-here.png
Updated the cache with the command from my earlier post.
Now have the foot replacing my "Main Menu" icon on the panel.
So for me at least, the original instructions still work in intrepid.

It is possible you aren't using the 24x24 icon set. You may have to experiment with putting the 'foot' icon in one of the other XxX folders.

Best of luck.

---

### Post by yamaman on 2009-12-18
Using Ubuntu 9.10, none of these methods worked for me, anyone got any other methods I could try. I have a black and green theme on my desktop, and that default icon just don't look right!

---

