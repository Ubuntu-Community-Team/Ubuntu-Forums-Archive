---
title: "problem with mp3?"
date: 2008-05-27
forum: New to Ubuntu
---

### Post by Sec Expert on 2008-05-27
hi 
when I try to run an mp3 or avi file it says "search for suitable codec" then it says "The playback of this movie requires a MPEG-1 Layer 3 (MP3) decoder plugin which is not installed." what should I do?:guitar:

---

### Post by dRock1286 on 2008-05-27
download ffmpeg from the repos...

---

### Post by billgoldberg on 2008-05-27
> **Sec Expert said:**
> hi 
when I try to run an mp3 or avi file it says "search for suitable codec" then it says "The playback of this movie requires a MPEG-1 Layer 3 (MP3) decoder plugin which is not installed." what should I do?:guitar:

Open a terminal and copy/paste this command:

```
sudo apt-get install ubuntu-restricted-extras
```

For other codecs (non-free, win32, dvd):

[http://linuxowns.wordpress.com/2008/02/11/media-and-ubuntu/](http://linuxowns.wordpress.com/2008/02/11/media-and-ubuntu/)

---

### Post by tom56 on 2008-05-27
The command above is the one you want. Try reading the manual though - I got this link from System -> Help and Support and searching for "codec". It was the second result.

[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

---

### Post by sayakb on 2008-05-27
[http://ubuntuforums.org/showthread.php?t=809005](http://ubuntuforums.org/showthread.php?t=809005)
Why did you create a separate thread ?? :confused:

---

