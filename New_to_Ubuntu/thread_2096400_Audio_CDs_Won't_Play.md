---
title: "Audio CDs Won't Play"
date: 2012-12-19
forum: New to Ubuntu
---

### Post by ajdrew06 on 2012-12-19
Hi All,

Some audio CDs will not play in either of my two machines with Ubuntu 12.04. When I insert the CD, I get the following dialog box:

Could not mount Audio Disc
Drive /dev/sr0 does not contain audio files

How can I get these CDs to play? The default application is Rhythmbox.

Thank you,
-drew

---

### Post by leclerc65 on 2012-12-19
That's must be the codecs.
Did you add the Medibuntu Repository ?
[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)
Hint: also do Google search for Restricted Extras, Non free codecs...

---

### Post by andrew.46 on 2012-12-20
Perhaps bypass the guis for a moment and try and play the cds with MPlayer from the commandline:

```

mplayer -cache 2048 -cache-min 80 cdda://

```

There is something so cool about that when it works :)

---

### Post by mastablasta on 2012-12-20
it probbaly mounts the CD in a different place. you need to first find out where. i too was suprised as linux seems to be unable to handle this simple task out of the box (i.e. find out that music cd is in and play music from it)

---

