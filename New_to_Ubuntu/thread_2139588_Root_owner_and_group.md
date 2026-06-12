---
title: "Root owner and group"
date: 2013-04-27
forum: New to Ubuntu
---

### Post by hiWorld on 2013-04-27
Could anyone tell me please how to change a file/directory owner and group from root to user?
Thanks for your feedback in advance

---

### Post by clearski on 2013-04-27
```
sudo chown newuser:newgroup file

```

---

### Post by Impavidus on 2013-04-27
Of course, only do this to files that have accidentally become root-owned. If you want convenient access to system files this is not a good idea.

---

### Post by 3rdalbum on 2013-04-27
> **hiWorld said:**
> Could anyone tell me please how to change a file/directory owner and group from root to user?
Thanks for your feedback in advance

Clearski gave you the right advice, but if you want to modify system files **this is the wrong way to do it**.

To modify system files, you need to start a program using "pkexec". If you wanted to edit the text file "/etc/X11/xorg.conf" using the Gedit text editor, you would do this:

```
pkexec gedit /etc/X11/xorg.conf
```

You can open a file browser as root; then when you double-click any files in that window they will be opened as root and any files you drag in will be copied across as root:

```
pkexec nautilus
```

ONLY open the files you need to open, or modify the folders you need to modify, when using programs as root.

---

