---
title: "HOWTO: Download Youtube Videos w/o conversion"
date: 2008-07-19
forum: Outdated Tutorials &amp; Tips
---

### Post by collinp on 2008-07-19
I am sure that many of you have saw a Youtube video that you wanted to keep, but you don't know how. Well, it is pretty simple:

[LIST=1]
[*]Open Firefox
[*]Browse to a Youtube video you want to keep
[*]Wait for the video to load entirely
[*]Navigate to /tmp
[*]look for a file with flash in it
[*]Right-click on the file, copy, then paste onto desktop/home folder
[*]Try to open the new flash file with Movie Player/Totem
[*]Movie Player/Totem will ask to install additional codecs, allow it to
[*]Attempt to play the video again. If it plays, everything worked out well.
[/LIST]
You may wish to rename the video file to something more recognizable because the default name is hard to remember. This is my first guide, so if you have any suggestions, post them.

**Suggested by Rhubarb:**

"It's also possible to use a nice CLI program called youtube-dl

```
sudo aptitude install youtube-dl

```Then just run it like so:

```
youtube-dl http://www.youtube.com/watch?v=Ke-kel9zOFo
```And you've got it in your home directory.
There are also some good command line switches you can use for it too.
Just run man youtube-dl for details of usage."
[B]
Suggested by aashay:[/B]

"I find the videos in my ff profile's cache folder @ ~/.mozilla/firefox/[profile]/cache
Just sort the listing by date. The video you just viewed will be at the bottom with a nice thumbnail to match it"

Thanks for the suggestions guys!

---

### Post by aashay on 2008-07-20
I find the videos in my ff profile's cache folder @ ~/.mozilla/firefox/[profile]/cache 
Just sort the listing by date. The video you just viewed will be at the bottom with a nice thumbnail to match it

---

### Post by Rhubarb on 2008-07-20
It's also possible to use a nice CLI program called youtube-dl
```
sudo aptitude install youtube-dl
```
Then just run it like so:
```
youtube-dl http://www.youtube.com/watch?v=Ke-kel9zOFo
```
And you've got it in your home directory.
There are also some good command line switches you can use for it too.
Just run **man youtube-dl** for details of usage.

---

### Post by collinp on 2008-07-20
Hmm, nice. Can i add these to my HowTo?

---

### Post by Rhubarb on 2008-07-21
> **Hellow said:**
> Hmm, nice. Can i add these to my HowTo?
Sure Hellow, no problem.

---

### Post by aashay on 2008-07-21
No problem

---

### Post by collinp on 2008-07-22
Ok thanks, ill add them now.

---

### Post by collinp on 2008-07-23
*Bump*

---

### Post by CSEatOSU on 2008-07-29
> **Hellow said:**
> I am sure that many of you have saw a Youtube video that you wanted to keep, but you don't know how. Well, it is pretty simple:

[LIST=1]
[*]Open Firefox
[*]Browse to a Youtube video you want to keep
[*]Wait for the video to load entirely
[*]Navigate to /tmp
[*]look for a file with flash in it
[*]Right-click on the file, copy, then paste onto desktop/home folder
[*]Try to open the new flash file with Movie Player/Totem
[*]Movie Player/Totem will ask to install additional codecs, allow it to
[*]Attempt to play the video again. If it plays, everything worked out well.
[/LIST]
You may wish to rename the video file to something more recognizable because the default name is hard to remember. This is my first guide, so if you have any suggestions, post them.

Worked like a charm, thanks!

---

### Post by 3rdalbum on 2008-07-29
If you don't use Adobe Flash Player, you can still download Youtube videos, but not through this method. You would need to use the website [www.downloadyoutubevideos.com](www.downloadyoutubevideos.com).

Also, the original HOWTO can be used for all other websites with Flash video.

---

### Post by Gourgi on 2008-07-29
> **Hellow said:**
> 
[*]Navigate to /tmp
[*]look for a file with flash in it
that's it ? :shock:
absolutely cool ! 
thanks for the tip 

:guitar:

---

### Post by SkonesMickLoud on 2008-07-29
If you use Firefox, click Tools >> Add-ons >> Get Add-ons and search for "DownloadHelper".  Install, restart FF, and look for a tri-colored bubble thing.  Click it and it'll let you download the video.

---

