---
title: "Get the new Cairo enabled Clearlooks here!"
date: 2005-11-11
forum: Outdated Tutorials &amp; Tips
---

### Post by Omer on 2005-11-11
[tirpse]("http://myeburg.net/") (aka SchAmane) made a Clearlooks gtk-engine patch to get animated progressbar and checkboxes using cairo.
Watch the demos for [animated checkbox]("http://files.myeburg.net/work/progressbar_anim/anim_checkbox1_xvid.avi"), [animated sliders]("http://files.myeburg.net/work/progressbar_anim/animated_slider.avi") and [animated progress bars]("http://files.myeburg.net/work/progressbar_anim/progress_anim.avi") (more demos available [here]("http://files.myeburg.net/work/progressbar_anim/")).

Check out his [blog entry]("http://myeburg.net/home/en/notes/show.8.html") to patch it by yourself, or simply download the attached DEB.

Just remove the file extension (.zip), and *dpkg* it:
```
sudo dpkg -i gtk2-engines-clearlooks_2.6.5-0ubuntu3_i386.deb
```

Package is patched against Ubuntu official package for maximum compatibility.
Works perfect on my machine, but still, in case of bugs, crashed, just roll back to official Ubuntu package.

Enjoy!

---

