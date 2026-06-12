---
title: "Problem with choppy videos (youtube, vlc...)"
date: 2020-08-02
forum: New to Ubuntu
---

### Post by sebastianbolivart on 2020-08-02
Hello, i am a newbie ubuntu user, i have been totally relate to windows all my life but now i want to use linux; a couple of weeks ago i have installed ubuntu 20 on my laptop, everything is ok except video playing that is choppy (lagging) on web like youtube and local like VLC. What can i do?

---

### Post by CatKiller on 2020-08-02
Browsers haven't had hardware accelerated video decoding until recently. If your CPU is weak it won't be able to keep up when doing it in software.

There have been builds of Chromium that are able to use hardware acceleration, and I believe the default build either has that now or will soon. Firefox should be getting it in the next version. 

VLC doesn't use hardware acceleration as far as I'm aware, but mpv does. 

Obviously your hardware acceleration capabilities will also be limited by the encoding of the media you're trying to play relative to the ability of your hardware to accelerate those encodings.

---

### Post by sebastianbolivart on 2020-08-02
Thank you for your answer, this is a picture of my pc specifications, i dont think it is weak (neither a rocket) i think it's good enought to play a video on youtube or vlc, in fact it did it in windows whit out problem. is it posible that is missing some codecs or software, that i have not installed?

[IMG]https://i.postimg.cc/GmsCSdQF/Captura-de-pantalla-de-2020-08-02-11-47-37.png[/IMG]

---

### Post by monkeybrain20122 on 2020-08-02
specs looks ok, I have a laptop with same cpu, an older intel HD card and less ram running Ubuntu 20.04 and I don't experience any lag. 

For local files, configure vlc to use vaapi for hardware accelerated decoding (Tools > Input & codecs, choose vaapi from the drop down window for hardware-accelerated decoding)  

You can run top in the terminal (open a terminal and type top) when you play a Youtube video and look at the cpu usage. It may also depend on your connection.

You can configure Firefox or Chrome to use hardware acceleration but won't work on Youtube videos because google encodes videos with v8/v9 codecs, there is an extension (available for Chrome and Firefox) called [h264ify ]("https://www.reddit.com/r/chrome/comments/2w2edu/h264ify_an_extension_that_makes_youtube_stream/")which forces the videos to be played in h264 for which hardware acceleration does work.

Also you can upgrade your graphic driver [https://launchpad.net/~kisak/+archive/ubuntu/kisak-mesa](https://launchpad.net/~kisak/+archive/ubuntu/kisak-mesa)

---

### Post by sebastianbolivart on 2020-08-07
> **monkeybrain20122 said:**
> specs looks ok, I have a laptop with same cpu, an older intel HD card and less ram running Ubuntu 20.04 and I don't experience any lag. 

For local files, configure vlc to use vaapi for hardware accelerated decoding (Tools > Input & codecs, choose vaapi from the drop down window for hardware-accelerated decoding)  

You can run top in the terminal (open a terminal and type top) when you play a Youtube video and look at the cpu usage. It may also depend on your connection.

You can configure Firefox or Chrome to use hardware acceleration but won't work on Youtube videos because google encodes videos with v8/v9 codecs, there is an extension (available for Chrome and Firefox) called [h264ify ]("https://www.reddit.com/r/chrome/comments/2w2edu/h264ify_an_extension_that_makes_youtube_stream/")which forces the videos to be played in h264 for which hardware acceleration does work.

Also you can upgrade your graphic driver [https://launchpad.net/~kisak/+archive/ubuntu/kisak-mesa](https://launchpad.net/~kisak/+archive/ubuntu/kisak-mesa)

**Thank you for your answer monkeybrain20122, the problem was solved upgrading the graphic driver as you indicated. I appreciate your help. **

---

