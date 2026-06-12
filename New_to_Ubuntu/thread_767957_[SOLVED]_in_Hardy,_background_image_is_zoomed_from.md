---
title: "[SOLVED] in Hardy, background image is zoomed from top left"
date: 2008-04-26
forum: New to Ubuntu
---

### Post by philphil on 2008-04-26
Hi,

I just upgraded to Hardy from Gutsy where I had a large photo set as my desktop background and it was on Zoom.  This worked nicely and the picture was zoomed in the perfect place, slap bang in the centre.  Following the reboot after the upgrade, my background picture is being zoomed (seemingly) from the top left so now the half of the picture I would like to see is being zoomed off the page :(

any ideas?

Thanks for your help.

---

### Post by stijngysemans on 2008-04-26
-Check your desktop background settings (right click your desktop, choose 'change desktop background'). Play a little bit arround with the style setting.

-Are you sure your screen resolution is setup correctly?

---

### Post by philphil on 2008-04-26
> **stijngysemans said:**
> -Check your desktop background settings (right click your desktop, choose 'change desktop background'). Play a little bit arround with the style setting.

-Are you sure your screen resolution is setup correctly?

hmm nope tried playing with the style setting and the screen resolution is fine.

I'd like to try to remove the photo and add it in again as a desktop background but I can't find the file anywhere and in "change desktop background" there seems to be no way of getting the "properties" of the file to find out where it is located.....Would this information be stored anywhere ? in a configuration file or something?

thanks for your help

---

### Post by Tulsapoke on 2008-04-29
I have the same problem on all my backgrounds.  I am not sure if this is a bug or if this was a conscious change.  Whatever it is it has made a few of my wallpapers look stupid.  I hope this is changed back soon.

---

### Post by philphil on 2008-05-02
did you try removing and then re-adding your background images to the list of jpegs that the desktop background chooser thingamajig stores

---

### Post by philphil on 2008-05-04
Well I found the file again, remove it from the desktop background options and re-added it but it's still zooming from the top left *not* from the centre :(

---

### Post by deruberhanyok on 2008-05-09
I had the same problem. There's a bug report here:

[https://bugs.launchpad.net/ubuntu/+source/gnome-desktop/+bug/197357](https://bugs.launchpad.net/ubuntu/+source/gnome-desktop/+bug/197357)

This has been fixed in the latest series of updates apparently.

---

### Post by philphil on 2008-05-10
lovely, that's fixed it, I'd actually installed the updates a couple of days ago but hadn't thought to check.  thanks!

---

