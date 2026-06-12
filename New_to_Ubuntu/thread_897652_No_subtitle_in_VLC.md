---
title: "No subtitle in VLC"
date: 2008-08-22
forum: New to Ubuntu
---

### Post by wariskampar on 2008-08-22
I have ensure that the name of .avi and .srt are the same (copy and paste). I even set auto detect subtitle in VLC preference. However, VLC still fail to display subtitle. On the other hand, TOTEM is ok and that only mean the subtitle is ok. What should be the problem?

---

### Post by Pro-reason on 2008-08-23
With some players, you have to have the subtitle file in the same directory, with the same name, and it will be used automatically.

But surely VLC works in a more logical way: you open the media file and the subtitle file separately.  They can be anywhere and called anything.

---

### Post by wariskampar on 2008-08-24
Hello, I do not know what to do next. Can someone at least share his/her SUbtitle Preference Setting because I think this maybe the culprit. I'm sorry to dig out this old forum but rather than open up new forum, I believe this is the best. Thanks in advance

---

### Post by wariskampar on 2008-08-24
I can only force VLC to display subtitle by providing the subtitle file name in the Preference. Before this it was automatically detected and I prefer it that way. I have make sure both files have the same names. I can alternatively use TOTEM which does not has this problem but I prefer VLC more. Can anyone kind enough to share VLC Subtitle configuration because I think that maybe the problem. Thanks in advance

---

### Post by wolfen69 on 2008-08-24
from [here]("http://ubuntuforums.org/showthread.php?t=210117&page=2") . "I changed the "Subtitles text encoding" to ISO-8859-1.
This option is available in Input / Codecs > Other codecs > Subtitles." hope this helps.

---

### Post by overdrank on 2008-08-24
Threads merged, please do not create multiple threads on the same issue. :)

---

### Post by Vivaldi Gloria on 2008-08-24
To fix the vlc subtitle issue press ALT+F2 and start

```
gksudo gedit /usr/share/applications/vlc.desktop
```

and change 

```
Exec=vlc %U 
```

to 

```
Exec=vlc %m
```

See

[http://ubuntuforums.org/showthread.php?t=775337](http://ubuntuforums.org/showthread.php?t=775337)

---

### Post by wariskampar on 2008-08-24
I've tried both method but problem persist. What should I do next:(

---

### Post by zyx on 2008-08-25
You can use kmplayer to show subtitle, kmplayer can handle most subtitle formats.

---

### Post by Bachstelze on 2008-08-25
> **wariskampar said:**
> However, VLC still fail to display subtitle.

VLC fails at a lot of things. Why do you want to use it if Totem works?

---

### Post by wariskampar on 2008-08-25
I assume this problem is solved. I followed Vivaldi instruction and set "Subtitles text encoding" back to Default. However, I notice VLC will only load subtitle automatically if I open the video within VLC (VLC>Quick Open Files..). If I right-clicked on the file, VLC refuse to load subtitle. 
As why I prefer VLC over TOTEM because I can access Context Menu while watching the film (right-clicked). TOTEM also freeze my system occasionally and I have to hard reboot everytime it happens. Those are a few reasons but most of all I am comfortable with VLC:)

---

### Post by billgoldberg on 2008-08-25
> **wariskampar said:**
> I have ensure that the name of .avi and .srt are the same (copy and paste). I even set auto detect subtitle in VLC preference. However, VLC still fail to display subtitle. On the other hand, TOTEM is ok and that only mean the subtitle is ok. What should be the problem?

In vlc, press "file -> open file".

There you can set the path to your subtitle.

It doesn't have to be the same name nor be in the same folder.

---

### Post by wariskampar on 2008-08-25
I prefer it to load automatically. If I pre-set the subtitle path (I do it if too desperate), I'll get error message when I open another film afterward. Thanks anyway

---

