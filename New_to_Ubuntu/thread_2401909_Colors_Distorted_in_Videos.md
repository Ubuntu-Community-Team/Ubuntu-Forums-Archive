---
title: "Colors Distorted in Videos"
date: 2018-09-24
forum: New to Ubuntu
---

### Post by trexmkii on 2018-09-24
Hi,

When using the default app for videos that came with ubuntu 18.04 the colors are completely distorted.
This problem only happens with the default app. VLC plays videos with no issues at all.
It's not a big deal since I can just use VLC but I was wondering if this can be resolved?

I attached a pic of the distorted video.

---

### Post by idkwhatimdoing1.0 on 2018-09-24
Hey there,

This is a common issue for most people when they download Ubuntu 18.04. The problem is (most of the times) Ubuntu's default app doesn't have the proper codecs or decoders. So basically they get a video file format it goes to open and it doesn't have a single clue what to do with it. Hence the extremely blurry 4K pixels. Hence why VLC works is because they have the necessary codecs and decoders to translate the amazing 4K pixel blocks into an actual video. The work around for this is simply installing the necessary files. Open the terminal and copy and paste the two lines down to download the necessary codec and decoders to watch the MPEG-4 videos.
 ```
sudo apt install libdvdnav4 libdvdread4 gstreamer1.0-plugins-bad gstreamer1.0-plugins-ugly libdvd-pkg
sudo apt install ubuntu-restricted-extras

```

hope this helps!

---

