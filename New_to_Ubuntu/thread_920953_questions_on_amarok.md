---
title: "questions on amarok"
date: 2008-09-15
forum: New to Ubuntu
---

### Post by fignig on 2008-09-15
okay so i want amarok to be my official music player. but i wanted to change a little something about it. when i'm looking through my music files and i want to play one i have to add it to the playlist before i can hear it. is there anyway to configure it so i can double click on the file and it starts auto playing?

---

### Post by nowshining on 2008-09-15
right-click an mp3 open-with check at the bottom remember app used, etc.. find the app in multimedia, highlight it and click ok. I personally use kaffeine for just listening to plain mp3s, etc.. then to hear my music collection I use amarok, and u can also go into amarok to auto-play last song on restart of the app.

---

### Post by mc4man on 2008-09-15
> when i'm looking through my music files and i want to play one......
If you mean looking thru your music files in amarok's gui - collection then somewhat no. The first one you click, d. click on, it will play, any others will be appended to the current list below current playing and or listed songs.

If you mean looking thru where your songs are stored, yes, you can do anything you want.

The simplest *first step* (towards doing anything you want) would be to set a 'custom' file association.

Right click on any **one example** of a song format. (mp3, flac, wav, wma, ect.

Go properties -> open with -> add -> use a custom command.  If you see amarok listed at any point **ignore**.

In the command box use this
```
amarok --load --play
```

Click *add* and exit out.

Now double left clicking on the format type you just set the properties on will remove any current playlist  (if any), load the song and begin playback.
If you d. left click on any other song of the same format the same thing happens.

If you have other formats follow the same method except this time as soon as you see 'amarok' with a **lowercase 'a'** choose it. (usually open with -> *add*. This is the amarok with your custom command vs. Amarok with the default command

note: the name 'amarok' (lowercase) can be changed if you wish as not to confuse with Amarok (uppercase

A little further explanation and link to some of the other ways to control amarok _outside of the gui._
[http://ubuntuforums.org/showthread.php?p=5766719#post5766719](http://ubuntuforums.org/showthread.php?p=5766719#post5766719)

---

