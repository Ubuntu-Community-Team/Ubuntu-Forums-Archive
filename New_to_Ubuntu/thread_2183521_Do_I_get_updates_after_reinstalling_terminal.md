---
title: "Do I get updates after reinstalling terminal?"
date: 2013-10-25
forum: New to Ubuntu
---

### Post by sha1sum on 2013-10-25
In the Ubuntu software center, I removed the gnome terminal. This gave me a warning, saying that if I remove the gnome terminal, I also don't get updates. Afterwards, I reinstalled it again. Do I now get the updates again?

---

### Post by fantab on 2013-10-25
Yes you will. The Software Center probably warned you about not getting updates for the removed terminal. 
I must ask why do you want to remove it?

---

### Post by sha1sum on 2013-10-25
Thank you for your reply, I appreciate it.

I reinstalled the gnome terminal because of problems described in this thread: [http://ubuntuforums.org/showthread.php?t=2183385](http://ubuntuforums.org/showthread.php?t=2183385)

---

### Post by mcduck on 2013-10-25
You should probably make sure that you still have the "ubuntu-desktop" package installed. Removing gnome-terminal would quite likely remove it as well, and it's sometimes required for updates (at least if you choose to upgrade to new Ubuntu release versiona t some point you definitely want to make sure you still have the desktop metapackage installed...)

---

### Post by sha1sum on 2013-10-25
I did some searching on how to see if a package is installed. I tried this:

```
~$ dpkg -s ubuntu-desktop
Package `ubuntu-desktop' is not installed and no info is available.
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.

```

Does this mean the package is not installed?

---

### Post by fantab on 2013-10-25
No, its not installed. Install it.

```
sudo apt-get update
sudo apt-get install ubuntu-desktop
```

---

### Post by sha1sum on 2013-10-25
Done. Thanks.

---

