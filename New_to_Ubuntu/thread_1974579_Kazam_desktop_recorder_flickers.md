---
title: "Kazam desktop recorder flickers"
date: 2012-05-06
forum: New to Ubuntu
---

### Post by jermza on 2012-05-06
Using Ubuntu 12.04 and installed Kazam. It's very polished and slick.

I've recorded my desktop a few times and have dropped the captured video into Kdenlive (which is better than Openshot - which crashes all the time - and Pitivi - which has very little to offer). 

After editing the captured video and exporting it, it seems to flicker as if it's picking up my monitor's refresh rate.

Any idea what this is?

---

### Post by llamabr on 2012-05-06
[https://bugs.launchpad.net/compiz-core/+bug/963093](https://bugs.launchpad.net/compiz-core/+bug/963093)

looks like you're right.  One solution seems to be not to run it fullscreen.  Another seems to be just to use straight ffmpeg:

[http://www.youtube.com/all_comments?v=mUIpqbH_i_c&page=1](http://www.youtube.com/all_comments?v=mUIpqbH_i_c&page=1)

---

### Post by NikTh on 2012-05-06
Hi , 
sorry to hear that for Openshot. I think its the best video editing program .

For kazam now , try to "play" with settings of Encoder type . Change it to : Gstreamer-H264/MP4 and see the result.

---

### Post by jermza on 2012-05-06
Seems to have the same result with RecordMyDesktop.

When playing Kazam / RecordMyDesktop videos BEFORE editing them, they play perfectly. But once edited and exported, there is a flicker no matter what extension I export to.

I didn't have this in 11.10, so I have no idea what it is.

---

### Post by NikTh on 2012-05-06
> **jermza said:**
> 
But once edited and exported, there is a flicker no matter what extension I export to.

Hi , 
try to install kdenlive from this PPA. --> [http://ppa.launchpad.net/sunab/kdenlive-svn/ubuntu](http://ppa.launchpad.net/sunab/kdenlive-svn/ubuntu) . I don't know exactly the differences but when i had problems (error to open the kdenlive) i installed via this PPA and works very good.
Thanks

---

