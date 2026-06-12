---
title: "Move all sub folders in a directory up one directory."
date: 2008-11-08
forum: New to Ubuntu
---

### Post by saj0577 on 2008-11-08
Recently I ripped and converted all my music and like a fool I told it to file in folders like so:

Artist Name/Album/Artist Name/Album


So is there anyway to copy the Artist Name (inside the Album Folder) and move it up 2 directories and delete the duplicated folders.


Hard to explain and understand not understand let me know.

Saj

---

### Post by keplerspeed on 2008-11-08
You could do a recursive move:

navagate to the first Album directory

> cd Artist\ Name/Album/

then move the second artist name directory to the music directory:

> mv -r Artist\ Name /home/yourname/music/

You can then delele the now empty first album directory:

> cd ..
rm Album

---

### Post by saj0577 on 2008-11-08
That would mean I have to cd into every directory which would not be time efficient. Anyway to do it to alot of folders at once.

Saj

---

### Post by earthpigg on 2008-11-08
open ~/My Music/Artist Name/Album/ select everything, and drag it to ~/My Music

merge all folders when it asks

or am i missing something?

---

### Post by bodhi.zazen on 2008-11-08
use find

[http://content.hccfl.edu/pollock/Unix/FindCmd.htm](http://content.hccfl.edu/pollock/Unix/FindCmd.htm)

find type -d ./ -exec /bin/cp -R '{}' ..;

---

### Post by saj0577 on 2008-11-09
> **earthpigg said:**
> open ~/My Music/Artist Name/Album/ select everything, and drag it to ~/My Music

merge all folders when it asks

or am i missing something?


That would work, but I have around 500 folders like this so doing it that way (manually) would take me ages.

Saj

---

