---
title: "Install VLC media player 0.9.2 in Ubuntu"
date: 2008-09-21
forum: New to Ubuntu
---

### Post by nhasian on 2008-09-21
I just upgraded from vlc 0.8.6 to 0.9.2 which adds a new Qt4 user interface, fullscreen controls, improved playlists, album art support, and new file format support.

To upgrade to the latest version of vlc follow these simple steps:

1) If you already have vlc installed, you need to remove it with
```
sudo apt-get remove vlc
```

2) Add the new repository. Open System->Administration->Software Sources->Third-Party Software
```
deb http://ppa.launchpad.net/c-korn/ubuntu hardy main
```

Close Software Sources, and when prompted, choose to reload the repositories.

3) Install the new version of vlc with:
```
sudo apt-get install vlc vlc-plugin-pulse
```

enjoy!

I found the steps to upgrade vlc from tombuntu.com I'm gonna have to add that site to my rss reader.

---

### Post by Vivaldi Gloria on 2008-09-21
Old news:

[http://ubuntuforums.org/showthread.php?t=920204](http://ubuntuforums.org/showthread.php?t=920204)
[http://blog.jetienne.com/2008/09/vlc-092-on-ubuntu-804.html](http://blog.jetienne.com/2008/09/vlc-092-on-ubuntu-804.html)

Thanks anyway.

---

