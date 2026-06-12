---
title: "[SOLVED] Hostname - How To Change?"
date: 2008-05-13
forum: New to Ubuntu
---

### Post by mapes12 on 2008-05-13
I need to now how to change my hostname. Any ideas please?

---

### Post by conscious on 2008-05-13
Just edit /etc/hostname:
```
gksudo gedit /etc/hostname
```

The change will be effective after reboot. To make immediate change, use
```
hostname
```

---

### Post by cyberbill on 2008-05-13
Used to be hostname, but looks like things changed somewhat.

This is an excerpt from a bug report, but very descriptive:

[https://bugs.launchpad.net/ubuntu/+source/hostname/+bug/113778/comments/7](https://bugs.launchpad.net/ubuntu/+source/hostname/+bug/113778/comments/7)

-cb

---

### Post by Zalbor on 2008-05-13
I'm not sure, but the simplest way is probably from System>Administration>Network>General. If the utility is made to work correctly, that should change it even if you're not sure which file to edit.

---

### Post by mapes12 on 2008-05-13
Thank you to all who replied. 

Editing the /etc/hostname file using gedit did the trick.

If only I knew the filesystem as well as you guys I wouldn't have to hang out on the forums for so long........but hey, I enjoy it!!  :)

---

### Post by inportb on 2008-05-13
Also, your hostname might be in your /etc/hosts file. It's not a big deal, but change it if you like completion ;p

---

