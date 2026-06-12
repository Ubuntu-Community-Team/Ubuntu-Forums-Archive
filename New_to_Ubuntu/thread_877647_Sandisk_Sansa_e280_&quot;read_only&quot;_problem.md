---
title: "Sandisk Sansa e280 &quot;read only&quot; problem"
date: 2008-08-02
forum: New to Ubuntu
---

### Post by VitaminBB on 2008-08-02
I have transferred podcasts already from ipodder to my sandisk mp3 player but just a few minutes ago I went to delete some podcasts off the mp3 player and I get this error ...

[B]"Error while deleting.
There was an error deleting _ _ _ _ _ .

Error removing file: Read-only file system"[/B]

This sucks ...

Btw it is in mass storage mode on the unit itself ...

---

### Post by hubie on 2008-08-02
Are you using an application to move files or are you just dragging and dropping (or using "mv" and "rm") them?

What does a directory listing of the e280 look like, in particular, what do the file permissions look like?

Can you delete them as root?

Your problem might be related to having journaling enabled; see [http://davesource.com/Solutions/20080225.iPod-linux-read-only.html]("http://davesource.com/Solutions/20080225.iPod-linux-read-only.html")

From these forums you can check out [this]("http://ubuntuforums.org/showthread.php?t=556750") or [this]("http://ubuntuforums.org/showthread.php?t=480658").

---

