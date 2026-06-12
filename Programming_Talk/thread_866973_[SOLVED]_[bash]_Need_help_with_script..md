---
title: "[SOLVED] [bash] Need help with script."
date: 2008-07-22
forum: Programming Talk
---

### Post by LinuX-M@n1@k on 2008-07-22
I have 100 songs in one folder, but every song ends with "[Torrent Tatty] **and more things here**". I need to make a script which replaces "[Torrent Tatty]*****" (***** is everything after Torrent Tatty), BUT including [Torrent Tatty].

Here's a song name for example:
> 002 - Mariah Carey - Touch My Body   [Torrent Tatty]  (&#8482; Island  IDJMG).MP3
Of course, I need to leave .MP3.

Any code will be MUCH appreciated since I'm not so good with bash ;).

Edit: Oh, and that "002 - " if possible too. Thanks!!!

---

### Post by arsenic23 on 2008-07-22
This should do it:

```
rename 's/\[Torrent\ Tatty\].*.*/\.MP3/' *
rename 's/\ *[.]MP3/\.MP3/' *

```

To get rid of the numbers at the beginning, the dash, and the spaces:
```
rename 's/^[0-9][0-9]*\ \-\ //' *
```


EDIT:
I'm asuming that all your files end in MP3 and not mp3.  If you have some lower case ones then you'll need to change the rename commands to this:

```
rename 's/\[Torrent\ Tatty\].*.*/\.mp3/' *
rename 's/\ *[.][mM][pP]3/\.mp3/' *
rename 's/^[0-9][0-9]*\ \-\ //' *
```

---

### Post by ghostdog74 on 2008-07-22
for systems without rename, just use substitution from sed/awk or bash 
```

a="002 - Mariah Carey - Touch My Body [Torrent Tatty] (™ Island IDJMG).MP3"
# echo $a | sed 's/\[Torrent.*.MP3$//'
002 - Mariah Carey - Touch My Body
# echo $a | awk '{gsub(/\[Torrent.*/,"")}1'
002 - Mariah Carey - Touch My Body


```

---

### Post by LaRoza on 2008-07-22
I found this "Torrent Tatty" is probably illegal (considering my ISP bans it, that is a bad sign...)

---

