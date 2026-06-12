---
title: "Create a Database file for you iRiver H1xx/3xx series players"
date: 2006-09-13
forum: Outdated Tutorials &amp; Tips
---

### Post by MetalMusicAddict on 2006-09-13
I stumbled across this little tool called [libiriverdb]("http://www.bodgit-n-scarper.com/code.html"). Its a library and utility to build the db file for you iRiver H1xx/3xx series players. It totally worked. :)

Heres how:

[LIST]
[*]Install the attached .deb I made from the .rpm with alien. (remove the ".zip" at the end first)
[*]Mount your player
[*]From a terminal type: iriverdb -help
[/LIST]
That will give you this:
[SIZE="1"]```
Usage: iriverdb [COLOR="Blue"][OPTION][/COLOR]... ACTION [COLOR="Red"]DIRECTORY[/COLOR]
Perform ACTION on iRiver jukebox mounted at [COLOR="Red"]DIRECTORY[/COLOR].

  [COLOR="Blue"]-d[/COLOR], [COLOR="Blue"]--database[/COLOR]=VERSION create specified version of the iRiver database.
                          Either this option must be specified, or use one of
                          the convenience options below for the specific
                          jukebox model
[COLOR="Blue"]--h300[/COLOR]               iRiver 20/40GB H300 series
[COLOR="Blue"]--h100[/COLOR]               iRiver 10/20/40GB H100 series
  [COLOR="Blue"]-v[/COLOR], [COLOR="Blue"]--verbose[/COLOR]  be verbose
  [COLOR="Blue"]-h[/COLOR], [COLOR="Blue"]--help[/COLOR]        display this help and exit
  [COLOR="Blue"]-V[/COLOR], [COLOR="Blue"]--version[/COLOR]   output version information and exit

ACTION can be one of `write', `refresh' or `read' to write a new database
from scratch, refresh an existing database, or dump the contents of an
existing database, respectively.

VERSION can be one of `0' or `1' corresponding to the 0.12 `8-bit string'
database found on H100 series jukeboxes, or the 0.16 `16-bit UTF string'
database found on H300 series jukeboxes.

Report bugs to <matt@bodgit-n-scarper.com>.
```[/SIZE]
[LIST]
[*]Build the db file.
[/LIST]
To build your db file you line in the terminal should look something like mine:
[SIZE="1"]```
iriverdb -v --h300 write /media/IRIVER\ H360
```[/SIZE]

So **iriverdb** is the app [COLOR="Blue"]-v --h300[/COLOR] are my options and [COLOR="Red"]/media/IRIVER\ H360[/COLOR] is the path to the root of my player. This should resault in a .db file at the root of your player that get read by your player on startup. ;)

Also I have just funded work for a front-end for this. Ill announce it later. Good Luck!

---

### Post by MetalMusicAddict on 2006-09-14
> **MetalMusicAddict said:**
> Also I have just funded work for a front-end for this. Ill announce it later. Good Luck!
I think we will have a test for the front-end out today if anyone would like to.

---

