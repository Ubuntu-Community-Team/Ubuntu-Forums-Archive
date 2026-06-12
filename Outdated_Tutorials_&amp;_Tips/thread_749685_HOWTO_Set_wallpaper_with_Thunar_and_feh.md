---
title: "HOWTO: Set wallpaper with Thunar and feh"
date: 2008-04-08
forum: Outdated Tutorials &amp; Tips
---

### Post by dbbolton on 2008-04-08
I've seen a couple tutorials on this forum that describe various ways that you can set the background from a file manager, but none quite as simple as this (no shell scripting whatsoever).

1. You must install thunar and feh, both of which are in the Ubuntu repositories.

2. Open Thunar. Go to Edit > Configure custom actions.

3. Click the + to add a new custom action.

4. "Basic" Tab. Set the name, description, and icon to anything you want.

5. Command !!! - Important - !!!

For Centered backgrounds:
```

feh --bg-center %f

```For Scaled backgrounds:
```

feh --bg-scale %f

```For Tiled backgrounds:
```

feh --bg-tile %f

```I recommend adding 3 separate custom actions, one for each type of wallpaper.

6. "Appearance Condition" Tab. In the "file pattern" field, just put *

7. Check "Image files" under "Appears if selection contains:"

8. Right-click on an image file in Thunar, and you can now set it as the background.



*** NOTES ***

You cannot use feh to set the background if your desktop environment is already managing the desktop.

You can have the background set automatically to the last image that feh used as the background by putting this in your start-up programs:

```
eval `cat $HOME/.fehbg` &

```(Thanks to urukrama for this tip.)

---

### Post by skip mcshwang on 2008-11-27
Those who use Gnome can use this in the Command field:

gconftool-2 --type str --set /desktop/gnome/background/picture_filename %f

(no feh required)

---

### Post by nephish on 2010-02-07
just found your post today, thanks

---

### Post by dE_logics on 2010-05-08
Thumbs up dude!

---

