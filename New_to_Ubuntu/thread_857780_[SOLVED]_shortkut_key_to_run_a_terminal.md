---
title: "[SOLVED] shortkut key to run a terminal"
date: 2008-07-12
forum: New to Ubuntu
---

### Post by adamogardner on 2008-07-12
not sure where to begin in choosing because i don't know all the other shortcuts.  any recommendations?  I will use it often so the more ergonomic the better.

---

### Post by Bodsda on 2008-07-12
The easiest way i found is to use ccsm (compiz config settings manager)

first make sure its installed

```
sudo apt-get install compizconfig-settings-manager
```

then run

```
ccsm
```

A window will pop up, click on the 'General Options' button, then go to the 'commands' tab, there is a section at the top for running 'gnome-terminal' and you can change the keyboard shortcut there.

Hope this helps

Bodsda

---

### Post by LaRoza on 2008-07-12
In the window manager I use (wmii), a terminal is just a "Alt + Enter" a way :-)

If you like keyboard control and efficiency, I suggest you try it.

---

### Post by aktiwers on 2008-07-12
System = Preferences = Keyboard shortcuts

And find "run a Terminal" and set a shortcut.

---

### Post by Dr Small on 2008-07-12
I use CTRL + ALT + t in Openbox.

---

### Post by boblemur on 2008-07-12
i use: ctrl + ` (ctrl + grave) i dono why ` is grave but thats what it says in my config file :P

i think its easy :P and from games or what eva im usto using ` for terminal... but 1 key shortcuts are neva really a good idea...

---

### Post by kansasnoob on 2008-07-12
Alt - F2 gets me this:

[ATTACH]77540[/ATTACH]

---

### Post by boblemur on 2008-07-12
if you are a windows convert then alt + f2 is like windows + r ( start > run)

but i think he wants a keyboard shortcut for teminal itself


although you can go alt + f2 tick run in terminal and run bash... but i like to have a separate key for it...

---

### Post by brennydoogles on 2008-07-12
I have two windows keys on my keyboard, so i set the right Windows key to open a new terminal, and the left to open my Home folder. This has worked out EXTREMELY well for me for almost 2 years now.

---

### Post by adamogardner on 2008-07-13
it's saying all the short cut options (the ones you gave me my fave being alt + enter   or ctrl = enter) are "invalid options"    I must be doing something wrong?

---

### Post by Jim! on 2008-07-13
> **LaRoza said:**
> In the window manager I use (wmii), a terminal is just a "Alt + Enter" a way :-)

If you like keyboard control and efficiency, I suggest you try it.

I've been using the terminal a lot more lately and that works great, Thanks!

---

### Post by ramjet_1953 on 2008-07-13
If you would like a quick-launch icon on your desktop, just do this:

1. Right-click on a blank area of your desktop. Then click on [COLOR="Blue"]Create Launcher.[/COLOR]

2. When the window opens type [COLOR="Blue"]Terminal[/COLOR] in the name field and [COLOR="Blue"]gnome-terminal[/COLOR] in the command field. An icon should be automatically selected.

3. Click on [COLOR="Blue"]OK[/COLOR].

You should now have an icon on your desktop to open a terminal.

Regards,
Roger :cool:

---

### Post by adamogardner on 2008-07-13
what is a window manager?  do I have one?  I must be entering the commands incorrectly.

---

### Post by TSS on 2008-07-13
Using the Windows key as a shortcut is brilliant haha.  I don't know why I never thought of mapping something to it before, must be a throwback from when I used Windows...

---

### Post by issih on 2008-07-13
If you are running stock ubuntu, the easiest way is just to edit the keyboard shortcuts from the preferences menu....some things aren't allwoed its true, but a lot are :)

Personally I use ctrl alt t to launch a terminal.

You can also set these things within compiz it is true, but setting it here means it works even if you fall back to metacity..

---

### Post by darco on 2008-07-13
Why dont you just add it to your panel?..Or if you have AWN, add it so it apprears on boot up.

darco

---

### Post by adamogardner on 2008-07-13
It is on my panel,  I made a tight little strip of five so I don't have to aim."

---

### Post by aktiwers on 2008-07-13
Did you try what I wrote? Works great here

---

### Post by tjwoosta on 2008-07-13
you would have to add your own shortcut in system-preferences-keyboard shortcuts


(i set mine to ctrl+t)

---

### Post by Inxsible on 2008-07-13
I use the following :

Windows (Super) + T = Terminal
Windows + M = Music player
Windows + W = Web Browser
Windows + F = File Manager
Windows + R = rtorrent (starting up in screen of course ;) )
Windows + D = Show Desktop
Ctrl + W = close

I only have 1 super key on the left side of the keyboard so you will notice that all the shortcuts except for the music player are keys on the left...One hand invocations ;)

---

### Post by adamogardner on 2008-07-13
i did it.  it is a bit sticky but it worked.  shift up for browser and shift menu for terminal.  thanks for the talk.

---

