---
title: "HOWTO: Speed, lower cpu usage of Rhythmbox"
date: 2007-02-01
forum: Outdated Tutorials &amp; Tips
---

### Post by davidY on 2007-02-01
Hi, I just noticed that my rhythmbox used about **~10%** just to play mp3s. Since this is ridiculous, I searched google for how to fix it. It turns out that one of the plugins is very inefficient. 

So I went into synaptic and uninstalled gstreamer-fluendo-mp3 and restarted rhythmbox. 

Now it uses **~1%** cpu power. It is possible (not that i see any differences) that I have disabled some ultra-awesome features like internet streaming mp3s or something like that.... except I don't use these features so it does not matter ^_^

If your rhythmbox fails to play, you should reinstall gstreamer-fluendo-mp3. There are no permanent changes, so don't worry about removing the library temporarily.

---

