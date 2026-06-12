---
title: "tabledit not executable with wine"
date: 2011-11-13
forum: New to Ubuntu
---

### Post by Dermot Doyle on 2011-11-13
Hi All,
I am trying to get tefview guitar tab software working with 10.04 and wine, but when I try to open the download I get:

The file '/home/dermot/Downloads/tefv.exe' is not marked as executable.  If this was downloaded or copied form an untrusted source, it may be dangerous to run.  For more details, read about the executable bit.

I am sure I had this working on this computer some time ago, probably with an earlier version of both Ubuntu and wine.

Any ideas?

---

### Post by skrizwanali on 2011-11-13
> **Dermot Doyle said:**
> Hi All,
I am trying to get tefview guitar tab software working with 10.04 and wine, but when I try to open the download I get:

The file '/home/dermot/Downloads/tefv.exe' is not marked as executable.  If this was downloaded or copied form an untrusted source, it may be dangerous to run.  For more details, read about the executable bit.

I am sure I had this working on this computer some time ago, probably with an earlier version of both Ubuntu and wine.

Any ideas?
you have to change the access permission of that file..for that you have to type the following command in your terminal
chmod 777 'filename'
or you can change the permission by going to the properties of that file and change the permision to read and write and it will work your way...gudluck..have fun

---

### Post by llamabr on 2011-11-13
Wine is very rarely the correct solution.  Even when it works, it does not tend to work well.  Instead, I usually try to find a native solution to whatever I'm trying to do.  For guitar tabs:

```
brock@vader:~$ apt-cache search guitar tab
chordii - Text file (chordpro format) to music sheet converter
etktab - ASCII guitar tab editor
exaile - flexible audio player, similar to Amarok, but written in GTK+
kguitar - Stringed instrument tablature editor for KDE
lilypond - A program for typesetting sheet music
songwrite - guitar tablature editor and player
tuxguitar - Multitrack guitar tablature editor and player (gp3 to gp5)
brock@vader:~$ 
```
And there's also:
[http://www.songsterr.com/](http://www.songsterr.com/)

---

### Post by Dermot Doyle on 2011-11-13
skrizwanali, thanks for that, I got it going.
llamabr, thanks also, I'll look into them as well.
Cheers

---

