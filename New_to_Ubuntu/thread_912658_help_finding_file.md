---
title: "help finding file?"
date: 2008-09-06
forum: New to Ubuntu
---

### Post by Daverobb on 2008-09-06
Can anyone help me to find the following file?

```
~/.config/xfce4/desktop
```

I've looked the filesystem but can't seem to find it.

---

### Post by annatar on 2008-09-06
The ~/ in the start of the pathname represents your home directory
e.g. if your user name is abc  
~/.config/xfce4/desktop = /home/abc/.config/xfce4/desktop

---

### Post by nkri on 2008-09-06
~/ means your home directory (/home/*yourusername*).

The dot before config means it's hidden, so to see it, you must go to your home directory (Places>Home Folder) and hit Ctrl+H.  You should now see a bunch of different files and folders with dots in front of their names.

Find the folder by either clicking in the white space and start typing ".config" (without the quotes), or manually look for it.

You could also search for it (Places>Search for Files...).  Where it says "Look in Folder," select your username (this is your home folder) and then search .config

Good luck!
-nkri

---

