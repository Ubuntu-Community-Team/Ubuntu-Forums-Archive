---
title: "Programms get uninstalled in the background"
date: 2012-02-05
forum: New to Ubuntu
---

### Post by Frozen Forest on 2012-02-05
EDIT:
I found the problem when trying to install zsnes again, when this is done will vlc get removed and since I installed vlc yesterday did zsnes get removed. Still how can I have both vlc and zsnes installed at the same time?

---

### Post by lechien73 on 2012-02-05
What version of Ubuntu are you running? Is it 64-bit? If so, adding this untrusted PPA and installing from there, by running the following code might help:

```
sudo add-apt-repository ppa:smaxein/ppa && sudo apt-get update && sudo apt-get install zsnes
```

Alternatively, if it is 64-bit, then the following patched version is supposed to work without installing VLC: [http://www.mediafire.com/?t9jwxm965gpicv7](http://www.mediafire.com/?t9jwxm965gpicv7)

---

