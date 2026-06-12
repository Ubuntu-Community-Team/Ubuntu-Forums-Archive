---
title: "Deluge bit torrent client?"
date: 2008-06-22
forum: New to Ubuntu
---

### Post by munkyboy on 2008-06-22
hello,

Im trying to get Deluge to work. but all that happens is i get the little egg timer and then nothing.

Ive tried everything i can think off does anyone know whats going on?

---

### Post by Nepherte on 2008-06-22
Try running it from the terminal (open up a terminal and type deluge). See if it gives any error messages in the terminal.

---

### Post by Drakkor on 2008-06-22
Or you can install 8.0.4 which has the "Transmission" bittorrent client built in,and works fine !  :)

---

### Post by munkyboy on 2008-06-22
Okay so i ran it in terminal.

It came up with this.

Traceback (most recent call last):
  File "/usr/bin/deluge", line 123, in <module>
    subprocess.Popen(["dbus-launch", "deluge"] + sys.argv[1:])
  File "/usr/lib/python2.5/subprocess.py", line 594, in __init__
    errread, errwrite)
  File "/usr/lib/python2.5/subprocess.py", line 1147, in _execute_child
    raise child_exception
OSError: [Errno 2] No such file or directory

Does any one know why there no such file or directory?

I tried transmission but it doesnt have some of the features I need. Whereas deluge does.

---

### Post by bred on 2008-06-22
[COLOR="RoyalBlue"]I've downloaded the last deluge from here 

[COLOR="Sienna"][http://deluge-torrent.org/downloads.php]("http://deluge-torrent.org/downloads.php")[/COLOR]

and everything is just fine..[/COLOR]

[COLOR="DarkRed"]u use kubuntu, u have ktorrent - a great bit-torrent program :)[/COLOR]

---

### Post by munkyboy on 2008-06-22
> **bred said:**
> [COLOR="RoyalBlue"]I've downloaded the last deluge from here 

[COLOR="Sienna"][http://deluge-torrent.org/downloads.php]("http://deluge-torrent.org/downloads.php")[/COLOR]

and everything is just fine..[/COLOR]

[COLOR="DarkRed"]u use kubuntu, u have ktorrent - a great bit-torrent program :)[/COLOR]

I have been using ktorrent but on certain trackers I get a stalled torrent. And wanted to change to another client cause these stalled torrents are annoying me.

EDIT;

Not sure how but i reinstalled it via Terminal and it works now. Its about the 5th time ive tried that.Nvm

---

