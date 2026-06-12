---
title: "No Video in VLC; Only Sound"
date: 2008-08-01
forum: New to Ubuntu
---

### Post by adobrakic on 2008-08-01
I don't know what the deal is, it used to work. Just stopped one day.
Now I used MPlayer, but the damn thing sucks. When I started a movie in VLC, i see the video for like a fraction of a second and it goes away. Any ideas? I like VLC a lot more than any of these other media players.

---

### Post by BGFG on 2008-08-01
Could try

```

sudo apt-get build-dep vlc

```

In case you recently installed another package that messed with vlc's dependancies.

---

### Post by mevets on 2008-08-02
This is a long shot, but you dont have Intel integrated graphics do you? I do and when I use compiz I get the same results. The fix is to change the video output module. Settings > Preferences > Video > Output modules > Check Advanced Options > Select X11 video output

---

### Post by BGFG on 2008-08-02
Saw some updates for intel related hardware recently. hope the intel guys get a reprieve now. I try to stay away from the stuff.

---

