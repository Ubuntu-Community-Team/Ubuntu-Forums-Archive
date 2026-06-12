---
title: "HOWTO: play all mp3s matching a pattern"
date: 2005-08-19
forum: Outdated Tutorials &amp; Tips
---

### Post by h-chi on 2005-08-19
this is just a very simple script i made for playing(enqueueing) mp3 files
matching a certain pattern with your favorite player.
it makes use of the **slocate** database, which indexes the files (according to permissions) on your computer.

if slocate isn't already installed type:
```

[COLOR=Green]sudo apt-get install slocate[/COLOR]

```
to build the index type:
```

[COLOR=Green]sudo slocate -u[/COLOR]
(this might take a while)

```
then create a new file containing:
```

[COLOR=green]#!/bin/bash
[COLOR=DarkRed]# folder where to store temporary playlist[/COLOR]
PLAYLIST=/tmp/playlist.m3u 
if [ $3 ]
then
        slocate -i $1 | grep -i $2 | grep -i $3 | grep [.]mp3 > $PLAYLIST
elif [ $2 ]
then
        slocate -i $1 | grep -i $2 | grep [.]mp3 > $PLAYLIST
elif [ $1 ]
then
        slocate -i $1 | grep [.]mp3 > $PLAYLIST
else
        echo "usage: playall <pattern1> [pattern2] [pattern3]"
        exit 0
fi

[COLOR=DarkRed]# your favorite player and the parameter for play/enqueue[/COLOR]
amarok -e $PLAYLIST 
#EOF[/COLOR]

```

change permissions for the file:
```

[COLOR=Green]chmod 755 *yourfilename*[/COLOR]

```
now you can either put a reference to the file in your **.bashrc** 
```

[COLOR=Green]gedit ~/.bashrc[/COLOR]

(add this to the existing alias definitions)
[COLOR=Green]alias playall='*pathtoyourfile*'[/COLOR]

```
or copy the file to a folder which is in your **PATH** variable.

now you can play, for example, all your mp3s of one artist from 1999 on a specific label (presumed you named your mp3s and your folders accordingly) by typing:
```

[COLOR=Green]playall *artist* 1999 *label*[/COLOR]

```

perhaps someone has some use for this.
it helped me alot to handle my mp3-collection.

---

### Post by lol on 2005-08-19
or you can give "Quod Libet" a try...

> Quod Libet is a music library management program. Rather than categorize songs by genre, artist, and album, it lets you search and display them however you want. It supports regexp-based searches, album cover display, tag editing, ReplayGain, multimedia keys, and an OSD. 

The regexp feature is really nice. Unfortunately, this is no Ubuntu package, but you can find one for Debian, or compile it...

[http://www.sacredchao.net/quodlibet](http://www.sacredchao.net/quodlibet)

---

### Post by h-chi on 2005-08-19
sounds interesting... i'll give it a try ....

----------------------------------------------------------------

i tested it.. but one big disadvantage is, that you can't search in filenames, but only in the id3 tags.
this assumes that you got all your tags right, which isn't the case for all of my files.
whereas the method via slocate searches the full pathnames of the mp3s and not
the tags. thus not depending on the correct id3 tags but on correct naming of the files and especially the folders.

---

