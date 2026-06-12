---
title: "HOWTO: Very simple way to manage wallpaper using Feh"
date: 2007-09-10
forum: Outdated Tutorials &amp; Tips
---

### Post by Kimm on 2007-09-10
I have recently started to look for ways to decrease memory usage on my computer (I'm a bit low on RAM). One thing that I have done is replace xfdesktop with feh.
The only thing that I found was missing when I did this, was a simple way to change my wallpaper, so I wrote a small (DE-independent) app and two scripts do do this for me.
Since I think this app would be perfect for people like me, or people using light DEs/WMs, I decided to share it with you :)

Also: This will not effect memory usage (only when you have the "wallpaper chooser" running)

[SIZE="5"]**Step 1:**[/SIZE]
Download: liten_0.1-1_i386.deb (see attachment) and install using:

```

sudo dpkg -i liten_0.1-1_i386.deb

```

Only requirements are libqt4-gui and feh.

[SIZE="5"]**Step 2:**[/SIZE]
You must make feh set your wallpaper automatically when you login (so that you dont have to do it manually). Depending on which DE/WM you are using, you have to do this differently.

The only thing you have to do, is ensure that the command:

```

minst

```

is executed as your DE/WM starts up. In XFCE you would do it this way:

Applications (XFCE Menu) -> Settings -> Autostarted Applications -> Add -> (set name and description to whatever you like) -> Command: minst

After this is done, liten will remember your last wallpaper, and apply it automatically when you login.

[SIZE="5"]**Step 3:**[/SIZE]
Make a launcher somewhere on your desktop that executes the command:

```

liten

```

This is the actual "wallpaper-chooser".

[SIZE="5"]**Volontary Step (File manager integration):**[/SIZE]
Another little advantage in using this method to set your wallpaper, is that it is easily integrated into file managers with custom actions, such as Thunar or Nautilus (Konqueror?). This is done using a helper script for liten (called: mindre)

**In Nautilus:**

open gedit and type:

```

#!/bin/bash

mindre $*

```

Then save as ~/.gnome2/nautilus-scripts/wallpaper.sh and run:

```

chmod  +x  ~/.gnome2/nautilus-scripts/wallpaper.sh

```

Then, rightclick on an image in nautilus, then select: scripts->wallpaper.sh 
This will set the wallpaper to that image 


**In Thunar:**

Edit->Configure Custom Actions -> + (add) -> Name: Set wallpaper -> Command: mindre %f -> (set the icon to whatever you want) -> Appearance Conditions -> Image Files (make sure this is the only thing checked)

Then rightclick on an image and select: Set wallpaper

[SIZE="5"]**Control using terminal:**[/SIZE]
If you refuse to use a filemanager, or liten you can use the terminal to set your background:

```

mindre <path to file>

```

[SIZE="5"]**Note:**[/SIZE]
No mather which method you use to set the wallpaper, liten will always remember which one you used last and apply it when you login.

If you want changes to the list saved, you must click on "Exit" when you close the application

[SIZE="5"]**Trivia:**[/SIZE]
Just thought I'd note: all names are swedish and mean:

Liten = Small
Mindre (invisible helper-script): Smaller
Minst = Smallest

---

### Post by Kimm on 2007-09-12
*bump*

---

### Post by jseiser on 2008-01-31
i was actually going to write a program similar to this and you did it for me :)  The only problem is that i see is libqt4-gui, is that qt file, or kde library file?  I wanted it to be gtk1 but beggers cant be choosers.

---

### Post by Kimm on 2008-02-08
> **jseiser said:**
> i was actually going to write a program similar to this and you did it for me :)  The only problem is that i see is libqt4-gui, is that qt file, or kde library file?  I wanted it to be gtk1 but beggers cant be choosers.

It has nothing to do with KDE. So no KDE libraries or processes will be loaded into memory :)

---

### Post by kerry_s on 2008-02-08
i usually would just use feh to do it.
feh -t ~/.backgrounds <- displays thumbnails, right click the thumb nail you want> set as background.
you have to click the 1 you want then right click to set.
(i usually make a right click command for that)(in thunar actions> feh -t %d <if i remember correctly)
(i've also on occasion just made a icon with that command)
(ps: you should read man feh, feh can actually do alot more, i use it as my image viewer-> [http://linuxbrit.co.uk/feh/wiki/FehHelp](http://linuxbrit.co.uk/feh/wiki/FehHelp) ) 

and of course, start up would have "eval `cat $HOME/.fehbg`" to load what ever background was last chosen.

i only have 1 background right now, but here's a pic anyway->

---

### Post by string158 on 2008-02-17
I have a folder ~/.backgound which stores any images which I use for the background.
I then have the following custom action in thunar:

cp %f ~/.background & feh --bg-scale ~/.background/%n

This copies the image into my background folder and uses feh to set the image as background. 

I then have:
 
eval `cat $HOME/.fehbg`

So that feh is draws the background on start up.

---

### Post by kerry_s on 2008-02-17
> **string158 said:**
> I have a folder ~/.backgound which stores any images which I use for the background.
I then have the following custom action in thunar:

cp %f ~/.background & feh --bg-scale ~/.background/%n

This copies the image into my background folder and uses feh to set the image as background. 

I then have:
 
eval `cat $HOME/.fehbg`

So that feh is draws the background on start up.

genius!

---

### Post by MediaMike on 2008-04-24
Okay, what am I doing wrong here.  I am running awesomewm and have configured my .xinitrc to run this command (which by the way work in a terminal) but when I restart X my background doesn't change.

feh --bg-scale ~/.background/1.jpg

the above works in a terminal when I type it in, but now when I set it in the .xinitrc or a script that .xinitrc calls during startup.

What gives?

---

### Post by kerry_s on 2008-04-24
put this in you ~/.xinitrc->
```
eval `cat $HOME/.fehbg` &
```

open your background in feh and use the set background option.
that's it your all set, it will load the last background used.

---

### Post by sercik on 2009-12-23
It is possible to have liten source?
i'm using a rpm based distro..
Hello

---

### Post by gldtn on 2010-07-14
I'm using openbox with feh and I have in my autostart.sh as follow;
(sleep 1 && .HOME/.fehbg) &

But it doesn't load the last bg I set.. I checked the .fehbg and it does have the name of the last bg set!

---

