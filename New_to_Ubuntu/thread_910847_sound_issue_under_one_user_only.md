---
title: "sound issue under one user only"
date: 2008-09-04
forum: New to Ubuntu
---

### Post by vampiricwound on 2008-09-04
well, while messing around with things i seem to have messed up the sound settings under one of my users (i have a separate username for my wife and i created a secondary one for myself after i started having issues) sound seems to work fine under both of the other users but not under my main one, i have no clue what i might have done but if i could find a way to copy the sound settings from one username to another it could solve my problem altogether

any help would be appreciated.

---

### Post by unutbu on 2008-09-05
All GNOME configuration (as far as I know) is done in four hidden dot directories in your home account: .config, .gconf, .gnome and .gnome2. If you rename these directories while not in GNOME, the next time you log in, GNOME will create new fresh ones, just like when you were a wee new user. 

Here are instructions on how to rename these directories while not in GNOME: [http://ubuntuforums.org/showpost.php?p=5312430&postcount=21](http://ubuntuforums.org/showpost.php?p=5312430&postcount=21)

It is possible that your loss of sound is due to some file/dir other than one of the four mentioned above, but perhaps try this first and see if it works. If it doesn't, the link also contains instruction on how to revert.

---

### Post by vampiricwound on 2008-09-05
well, it halfway worked, i now have sound in most things (such as games under wine, or if i play a sound file/mp3) but i am back to the original problem that caused me to mess with things in the first place, i mysteriously lost sound in flash, ive done some searching and tried a few things apparently one of those things wiped all sound capability on just the one username (oddly i can watch flash videos on the other users)

if it matters/helps, im running ubuntu 8.04 and firefox 3.0.1

and thanks again for your help thus far unutbu


hmmm......apparently the video i tested with wasnt quite working right to begin with.....because i tried a different video (actually wasnt anticipating to have sounds.....scared the crap outta my wife since the volume was up a wee bit higher than normal :p) and it works, thanks again and hopefully i wont be having these sound issues anymore...

---

