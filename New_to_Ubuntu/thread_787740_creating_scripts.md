---
title: "creating scripts"
date: 2008-05-09
forum: New to Ubuntu
---

### Post by oarking on 2008-05-09
i just installed ubuntu hardy. it's been a long time coming but i finally decided to build my own computer and just fly blind. it feels really good. i'm learning BASH from some of the awesome threads and links on here, but i had a question about how to create macros (i.e. automator on a mac).

say i want to create a script that organizes my music folder. i would have it look in the ID3 tag for artist and album, then put the songs in the album folders, the album folders in the artist folder, then in the music folder; much like itunes. i realize that there are probably programs out there like amarok that do it automatically, but i'm starting from scratch as much as i can.

---

### Post by hyper_ch on 2008-05-09
do you have any program that can read the id3 tag from the CLI?

---

### Post by sdennie on 2008-05-09
Installing the id3 program would be a good start:

```

sudo apt-get install id3

```

Then you can say:

```

id3 -l some_song.mp3

```

You'll want to look into the "cut" command or possibly "sed" or "perl" to parse the output.  After that, the only real gotcha would be that the id3 tags are likely to have spaces in the names and so you'll have to deal with that properly.

---

### Post by ibuclaw on 2008-05-09
**mp3info** is also good for the job too.
Although a little more selective, you can pick and choose what you wish to read.

ie:
A random example to show you the possibilities:
[PHP]
mp3info -p "Artist(%%a): %a\nTrack Title(%%t): %t\nTrack Number(%%n): %n\nAlbum Name(%%l): %l\nGenre(%%g): %g\nYear(%%y): %y\nTotal Duration(%%S): %S\nBitrate(%%r): %r\nNumber of Corrupt Audio Frames(%%b): %b\n\n" *.mp3
[/PHP]

Regards
Iain

---

### Post by oarking on 2008-05-09
ok, is there a way to do something like "if artist is 'tool' then put in folder 'tool'" and from there (inside the tool folder) do "if album is 'aenima' put in folder 'aenima'"? but have it do that for all the songs not just tool. still not sure how to word it right... create folders by artist, then inside those folders create folders by album. does that make sense?

---

### Post by PeterJS on 2008-05-09
> **oarking said:**
> ok, is there a way to do something like "if artist is 'tool' then put in folder 'tool'" and from there (inside the tool folder) do "if album is 'aenima' put in folder 'aenima'"? but have it do that for all the songs not just tool. still not sure how to word it right... create folders by artist, then inside those folders create folders by album. does that make sense?

This is going to be rough, dirty and have pusedo code and mistakes in it, but it should be a push in the right direction:
```

#/bin/bash

SOURCE="~/music"
DEST="~/new_music"

MUSIC_FILES=`ls SOURCE`
for SONG in $MUSIC_FILES
do
ARTIST=`someid3magic $SONG`
ALBUM=`someid3magic $SONG`
#Probably some tag clean up
mkdir -p "$DEST/$ARTIST/$ALBUM/"
mv "$SOURCE/$SONG" "$DEST/$ARTIST/$ALBUM/$SONG"
done

```

The big thing is that you can grab the artist/album for each track, create a directory for that combination and then move (or copy, or link) the songs there. Pieces that need to be filled in are how to handle/get the id3 tags and any clean up they may need, and fixing any syntax or other mistakes as I didn't tests that. The idea's good, the code is probably bad.

---

### Post by mlentink on 2008-05-09
> **oarking said:**
> ok, is there a way to do something like "if artist is 'tool' then put in folder 'tool'" and from there (inside the tool folder) do "if album is 'aenima' put in folder 'aenima'"? but have it do that for all the songs not just tool. still not sure how to word it right... create folders by artist, then inside those folders create folders by album. does that make sense?

[linuxcommand.org]("http://gd.tuwien.ac.at/linuxcommand.org/writing_shell_scripts.php") can teach you how to write scripts

---

