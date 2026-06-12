---
title: "where are program files stored on ubuntu 20.04?"
date: 2022-01-08
forum: New to Ubuntu
---

### Post by ruby9 on 2022-01-08
Just recently made the switch from 16.04 on my laptop and want to update VLC and install new brushes and fonts on gimp but can't find where the program files are. They used to be in   /usr/lib but in 20.04 there not there? Where do I look?

---

### Post by KBar on 2022-01-08
GIMP by default creates directories in its own directory *$HOME/.config/GIMP/$(gimp --version | cut --delimiter=' ' --fields=6 | cut --delimiter='.' --fields=1,2)*

I don't know about VLC but any application that strives for consistency and conformance usually places user-specific data and configurations in appropriate subdirectories in user's home directory.

---

### Post by ruby9 on 2022-01-08
I've looked in  *$HOME/.config/ *but it's not there, I installed it via the ubuntu software store, could it have installed anywhere else?

---

### Post by KBar on 2022-01-08
Check under *Edit* &#8594; *Preferences* &#8594; *Folders* tab.

---

### Post by CatKiller on 2022-01-08
> **ruby9 said:**
> I've looked in  *$HOME/.config/ *but it's not there, I installed it via the ubuntu software store, could it have installed anywhere else?
Did you perhaps install the snap version? That would have its own structure, since snaps are sandboxed from everything else.

---

### Post by tea for one on 2022-01-08
> **ruby9 said:**
> Just recently made the switch from 16.04 on my laptop and want to update VLC

Assuming you have the deb version of vlc, open a terminal and enter:-
```
sudo apt upgrade vlc
```

---

### Post by ruby9 on 2022-01-08
I went to home config then clicked on preferences and a pop up window with views, behavior, list columns, search & preveiw tabs turns up, I can't find folders.

---

### Post by ruby9 on 2022-01-08
Not intentionally, I just installed 20.04 version and went to the ubuntu software app to install a few other programs, how would I check to see if I have snap installed?

---

### Post by CatKiller on 2022-01-08
> **ruby9 said:**
> Not intentionally, I just installed 20.04 version and went to the ubuntu software app to install a few other programs, how would I check to see if I have snap installed?
It probably says in the Software Store application (I don't use it), or you could use ```
snap list
``` and see if those applications are listed.

---

### Post by ruby9 on 2022-01-08
I typed snap list into the terminal, this is what came up: 
snap list
Name               Version                     Rev    Tracking         Publisher         Notes
bare               1.0                         5      latest/stable    canonical&#10003;        base
brave              1.34.80                     141    latest/stable    brave             -
core18             20211028                    2253   latest/stable    canonical&#10003;        base
core20             20211129                    1270   latest/stable    canonical&#10003;        base
gimp               2.10.28                     383    latest/stable    snapcrafters      -
gnome-3-28-1804    3.28.0-19-g98f9e67.98f9e67  161    latest/stable    canonical&#10003;        -
gnome-3-34-1804    0+git.3556cb3               77     latest/stable/&#8230;  canonical&#10003;        -
gnome-3-38-2004    0+git.cd626d1               87     latest/stable    canonical&#10003;        -
gtk-common-themes  0.1-59-g7bca6ae             1519   latest/stable/&#8230;  canonical&#10003;        -
snap-store         3.38.0-66-gbd5b8f7          558    latest/stable/&#8230;  canonical&#10003;        -
snapd              2.53.4                      14295  latest/stable    canonical&#10003;        snapd
telegram-desktop   3.4.3                       3544   latest/stable    telegram.desktop  -
vlc                3.0.16                      2344   latest/stable    videolan&#10003;         -

---

### Post by KBar on 2022-01-08
> **ruby9 said:**
> I went to home config then clicked on preferences and a pop up window with views, behavior, list columns, search & preveiw tabs turns up, I can't find folders.

You do that from within **GIMP**.

---

### Post by KBar on 2022-01-08
> **ruby9 said:**
> I typed snap list into the terminal, this is what came up: 
snap list
Name               Version                     Rev    Tracking         Publisher         Notes
gimp               2.10.28                     383    latest/stable    snapcrafters      -
vlc                3.0.16                      2344   latest/stable    videolan&#10003;         -

Consider using code tags.

Both applications are snaps. Snaps store their user configuration files in *$HOME/snap*. You can find the exact location of its directories from within GIMP.

---

### Post by mIk3_08 on 2022-01-08
> **ruby9 said:**
> Just recently made the switch from 16.04 on my laptop and want to update VLC and install new brushes and fonts on gimp but can't find where the program files are. They used to be in   /usr/lib but in 20.04 there not there? Where do I look?
your vlc is on the snap folder. just take a look at there. And maybe you can update it via snap command in your terminal. so Good Luck and Cheers.

---

### Post by ruby9 on 2022-01-08
> **KBar said:**
> You do that from within **GIMP**.

Thanks, I checked it's in a folder in the home folder called snap, opening the gimp folder in snap everything looks really different than I'm used too, found the brush folder but it's empty (GIMP itself is working fine though)

---

