---
title: "Help wanted"
date: 2009-02-25
forum: Programming Talk
---

### Post by Ferrat on 2009-02-25
Well just found out that with newer versions of wine, uTorrent can handle argument from terminal 

 ```
env WINEPREFIX="/home/$USER/.wine2" WINEDEBUG=-all wine "C:\Program Files\uTorrent\uTorrent.exe" "[COLOR="Red"]**Z:$path$file**[/COLOR]"
```

If utorrent is running it will just add the torrent as if it was added in windows and if not running it will start up and add it.

Where Z: is the wine label for / , that's the part that really needs some work just getting the file path :) if possible in a  FF/Gnome/nautilus combo?

I suck at bash, really suck, haven't looked at it much, might do some day but wondering is it possible to use this to write a script that can get the torrent file from /tmp (where firefox puts it) while using it as a "Open with" selection? 

Really hate saving all the torrent files to my desktop and adding them manually and this would be a real treat, it seems fairly easy to do, just use the $NAUTILUS_PATH from the file thingy and put it in but as I said, haven't got a clue, looked around a bit but was really hoping if it wasn't to hard if someone could scribble something together? 

more or less all it has to do is send the code above with file and path taken from /tmp via the Open with :) 

I'm a bit tired so hope you can understand it anyway :P

---

### Post by cerealtx on 2009-02-25
why use utorrent in the first place....

---

### Post by Ferrat on 2009-02-25
> **cerealtx said:**
> why use utorrent in the first place....

A bit of topic but because it uses very little resources, is fast, easy and got good functionality, haven't found anything native that can do the job just as well, either they are lacking functions or eating resources.

---

