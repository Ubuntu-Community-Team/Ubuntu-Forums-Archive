---
title: "help with cmus"
date: 2013-02-22
forum: New to Ubuntu
---

### Post by rburkartjo on 2013-02-22
i have my music on an external hard drive. i want to play it with cmus(a terminal media player). i can get my music to play after i open it. however if i open an album cant figure out how to make it play all the song in the album with out selecting each one separately. maybe it cant be done. have read the man but that didnt help. tks

---

### Post by Sealbhach on 2013-02-22
Seems you have to toggle play next track by press Shift + C.

See here: [https://github.com/cmus/cmus/blob/master/Doc/cmus-tutorial.txt](https://github.com/cmus/cmus/blob/master/Doc/cmus-tutorial.txt)

> 

cmus has some great options to control what plays next (if anything) when the
track ends. The state of these settings are shown in the bottom right corner.
The first of these shows what collection of tracks (currently "all from
library") we are playing. Press *m* to cycle through the different options for
this setting. To the right of that (past the "|") cmus shows the state of three
toggles. Only toggles which are "on" are shown, so now we only see the *C*.
Here are the toggles:


[C]ontinue


    When this is off, cmus will always stop at the end of the track. You can
toggle this setting by pressing *shift-C*.


---

### Post by Toz on 2013-02-22
If you are in browser mode (5), you can highlight the album and press 'y' to add the whole album to the playlist (3). 

You can also use cmus-remote (man cmus-remote):
```
cmus-remote -c /path/to/album/*.mp3
```
...to do the same as above from a terminal (note: the '-c' will clear the playlist before adding the tracks to it. If you don't want it cleared, then omit the '-c').

You can do the same from the library mode (1). Press 'y' on either the group name or the album name to add all the songs from those respective levels (all group songs or all album songs).

---

### Post by rburkartjo on 2013-02-22
seal and toz tks

---

