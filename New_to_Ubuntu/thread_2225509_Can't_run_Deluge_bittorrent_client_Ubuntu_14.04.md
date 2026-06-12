---
title: "Can't run Deluge bittorrent client Ubuntu 14.04"
date: 2014-05-21
forum: New to Ubuntu
---

### Post by NA3OH on 2014-05-21
Error msg when I try to run deluge from the terminal

```

[ERROR   ] 18:58:20 ipcinterface:156 Deluge restart failed: Couldn't listen on any:/home/nick/.config/deluge/ipc/deluge-gtk: Cannot acquire lock.

```


It's been working fine for weeks, now just all of a sudden it won't work. I've tried uninstalling and reinstalling but to no avail.

Posting this in Absolute Beginners Section because I am an absolute beginner

---

### Post by sandyd on 2014-05-21
> **NA3OH said:**
> Error msg when I try to run deluge from the terminal

```

[ERROR   ] 18:58:20 ipcinterface:156 Deluge restart failed: Couldn't listen on any:/home/nick/.config/deluge/ipc/deluge-gtk: Cannot acquire lock.

```


It's been working fine for weeks, now just all of a sudden it won't work. I've tried uninstalling and reinstalling but to no avail.

Posting this in Absolute Beginners Section because I am an absolute beginner

Try
```

rm -rf ~/.config/deluge/ipc
```

please copy/paste - if you make a space in between the path, it may wipe out other things that you dont want to wipe out.

---

