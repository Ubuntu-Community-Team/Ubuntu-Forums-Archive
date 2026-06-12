---
title: "[SOLVED] I'm look for a video-capture app"
date: 2008-05-31
forum: New to Ubuntu
---

### Post by Bigtime_Scrub on 2008-05-31
Im looking for something that can rip you-tube videos? Anybody know any good apps that can do this?

---

### Post by spiderbatdad on 2008-05-31
the best I have found is in the repos: youtube-dl```
sudo apt-get install youtube-dl
```It is a command line tool. saves the vid as flash (flv) files, and plays them back without loss of quality.
For example:```
 youtube-dl -o /home/username/filename.flv http://www.youtube.url

``` just substitute your username, the filename, and paste a real url into the line.

---

### Post by TeoBigusGeekus on 2008-05-31
If you are using Opera, all videos you watch on youtube or any other site are saved in the ~/.opera/cache4 folder. Just rename them to whatever.flv
and you are done.

---

### Post by Bigtime_Scrub on 2008-05-31
Thanks. That worked pretty good.

---

### Post by koshari on 2008-05-31
or otherwise just drop the youtube url in keepvid.com and it will allow you to save.

---

### Post by imT on 2008-05-31
go to "/tmp" :popcorn:
wait for the file to be loaded and then get it from "/tmp"

---

