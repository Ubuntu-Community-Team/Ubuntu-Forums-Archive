---
title: "desktop copying"
date: 2013-07-04
forum: New to Ubuntu
---

### Post by bdubawoop on 2013-07-04
just installed 12.04lts

2 questions re copying:

1-can the cntrl-c & cntrl-v thing be made to work.

2-permissions? i had copied the background images from 10.04 to another partition.
after installing i went there, selected everything, right click & copy but when i went to /usr/share/backgrounds i was unable to paste.

whats the best way to copy in the desktop? chown /usr/share/backgrounds?

---

### Post by deadflowr on 2013-07-04
You need root
easy way is
```
sudo cp file-i-want-to-copy /usr/share/backgrounds
```

---

### Post by mardybear on 2013-07-05
...or if you prefer a GUI method to cut/copy via root, simply enter gksu nautilus (or whatever file browser you utilize).

mardybear

---

### Post by bdubawoop on 2013-07-05
thanks, i ended up using the terminal & sudo

ill check out nautilus, desktop has the advantage of not having to know/type out the paths.
.

---

### Post by dannyboy79 on 2013-07-05
just be VERY CAUTIOUS launching Nautilus with "gksudo" or "gksu" because that means you have a GUI file manager with root privalages meaning if you accidentally drag and drop a folder it won't warn you, it'll just do it. So whenever I launch Nautilus with gksudo as soon as I am done doing what I wanted I close that nautilus window.

ctrl-c and ctrl-v can work as long as you have permissions to wherever you're trying to paste to. In that case the /usr/share/backgrounds is owned by root so you don't have permissions to write there.

---

