---
title: "firefox.tmp folder- curious what it is"
date: 2022-05-13
forum: New to Ubuntu
---

### Post by jonfisher on 2022-05-13
firefox.tmp folder keeps showing up in my download folder.
last time with a folder inside it named "Temp-2a92fcd2-963a-4d39-a772-af1285d3c21b"
I keep deleting.
just curious what it is

---

### Post by #&amp;thj^% on 2022-05-13
I'll add this, When downloading a file (any file), the file is created with a temp name
in the /tmp dir. 
Firefox snap uses following directory for firefox.tmp

TMPDIR=$(xdg-user-dir DOWNLOAD)/firefox.tmp

see - [https://searchfox.org/mozilla-release/source/taskcluster/docker/firefox-snap/tmpdir](https://searchfox.org/mozilla-release/source/taskcluster/docker/firefox-snap/tmpdir)

To change the personal DOWNLOAD directory edit the file ~/.config/user-dirs.dirs

you can check the value with

```
xdg-user-dir DOWNLOAD
```

---

