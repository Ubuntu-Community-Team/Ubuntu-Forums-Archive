---
title: "places menu and the storage device manager"
date: 2008-10-31
forum: New to Ubuntu
---

### Post by ginestre on 2008-10-31
Why do my various partitions show up in  in /media and in the storage device manager, but not in the Places menu?

---

### Post by ashmew2 on 2008-10-31
> **ginestre said:**
> Why do my various partitions show up in  in /media and in the storage device manager, but not in the Places menu?

Hello , 
I dont know WHY it is happening , but i think it can easily be fixed by :

1) Open the /media folder in Nautilus.
2) Drag the Partitions you want to appear in the Places Menu on the left hand side (the side pane).

You can also remove anything from the side pane.
Your places menu will be updated accordingly.

See attached thumbnail !

---

### Post by kaivalagi on 2008-11-01
There is a launchpad bug for this: [https://bugs.launchpad.net/ubuntu/+s...us/+bug/260492](https://bugs.launchpad.net/ubuntu/+s...us/+bug/260492)

In summary, the best fix is to edit ~/.local/share/applications/mimeapps.list removing the offending ?.desktop entries against the inode/directory entry.

e.g. from:
```

inode/directory=userapp-baobab-OO53FU.desktop;nautilus-folder-handler.desktop;nautilus.desktop;userapp-nautilus-XXZ2JU.desktop;
```

to:

```
inode/directory=nautilus-folder-handler.desktop;
```

There is no need to go through all the places bookmarked changing the "open with" options

---

### Post by k3lt01 on 2008-11-01
> **kaivalagi said:**
> There is a launchpad bug for this: [https://bugs.launchpad.net/ubuntu/+s...us/+bug/260492](https://bugs.launchpad.net/ubuntu/+s...us/+bug/260492)This link does not work, for me anyway.

---

