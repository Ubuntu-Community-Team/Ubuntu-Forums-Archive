---
title: "Music player + youtube = no worky"
date: 2008-09-02
forum: New to Ubuntu
---

### Post by adobrakic on 2008-09-02
I have Linux Mint. (this is been my opening statement for my past, like, 50 threads)
I've tested this with Songbird and Banshee. Whenever I have either of those open, my youtube videos won't work. Either they'll be just gray boxes on forums, or on the actual website they'll have no sound and stop working after it gets to 2 seconds.

Any ideas? I initially thought it was a Flash problem, but I tried downgrading to java5 with no luck. I also uninstalled gnash or whatever it's called.

---

### Post by bawilson2 on 2008-09-02
Could be a possible solution here.

[http://ubuntuforums.org/showthread.php?t=906294](http://ubuntuforums.org/showthread.php?t=906294)

---

### Post by adobrakic on 2008-09-02
In gstreamer-properties my default output plugin is Alsa, and the test works when I have banshee playing. My input never plays when I press test, and I also have that set to alsa.

As for the video part, my default output is set to autodetect and the test works. but my default input is set to Video for Linux2 (v4l2) and I get the following error when trying to test it:

```
Video for Linux2 (v4l2): Cannot identify device 'dev/video0'
```

I can change it to 'Test Input' and then the test works fine, although idk what this would help.

---

### Post by adobrakic on 2008-09-03
bump

---

