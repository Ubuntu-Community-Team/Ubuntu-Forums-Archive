---
title: "Taskbar and start menu problem"
date: 2008-06-13
forum: New to Ubuntu
---

### Post by sxytrillian on 2008-06-13
i cannot able to view taskbar and start menu i.e where it will show application,places, system all in my computer.please help how i can restore it back.its showing only the folders in my desktop nothing else..

help me out..

thanks..

---

### Post by PurposeOfReason on 2008-06-13
You mean the panels? Press Alt+F2 and type in gnome-panel.

---

### Post by _sphinx_ on 2008-06-13
May be that the panel is already running in the background so writing in Alt+F2, gnome-panel may not work, I am not sure here. Better to first kill the panel by writing ```
killall gnome-panel
```
then write in terminal
```
gnome-panel &
```

---

### Post by pastalavista on 2008-06-13
try booting in recovery mode and repair xorg-conf

---

### Post by PurposeOfReason on 2008-06-13
> **pastalavista said:**
> try booting in recovery mode and repair xorg-conf
It won't be his xorg because he can enter an X session and the problem isn't dealing with graphics so he doesn't need to modify it at all.

---

### Post by sxytrillian on 2008-06-13
sphinx your method worked but if i close the terminal once again all get disappeared and if i type killprocess gnome-panel in terminal its displaying the message no kill process..

And tell where to write the "killall gnome-panel" code?

---

### Post by sxytrillian on 2008-06-13
i have typed killall gnome-panel in terminal.

when i type killall gnome-panel its showing the following message

"gnome-panel : no process killed"

---

### Post by _sphinx_ on 2008-06-13
Ok your gnome-panel is not running, do youneed not to kill that, and so as PurposeOfReason says, Hit Alt+F2 and type:
```
gnome-terminal
```
this should work

---

### Post by sxytrillian on 2008-06-13
its also not working when i close the terminal all get disappeared.

in terminal its showing the following error

$ gnome-panel &
[2] 6367
[1]   Terminated              gnome-panel
~$ 
(gnome-panel:6367): Wnck-WARNING **: Property _NET_WM_NAME contained invalid UTF-8

Please guys help me out to get rid of this..

---

### Post by _sphinx_ on 2008-06-13
Oh I am really sorry for my typo hit Alt+F2 and write
```
gnome-panel
```
You need not open any terminal.

---

### Post by sxytrillian on 2008-06-13
but still no use guys. its disappearing again..

any valid method to restore back again?

---

### Post by sxytrillian on 2008-06-13
hey guys help me out..

---

### Post by SunnyRabbiera on 2008-06-13
did you try a restart?
also you may need to reinstall gnome desktop and remove a few config files

---

### Post by pastalavista on 2008-06-14
I'm sorry, I misspoke. What I was thinking of was to try:
```

sudo gconf-editor
```

something might be checked or unchecked in there. I'm probably more of a noob than you are...

---

