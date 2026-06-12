---
title: "deleting utorrent (files)"
date: 2012-08-09
forum: New to Ubuntu
---

### Post by mahmut999 on 2012-08-09
I blindly tried to install utorrent to my computer. I followed instructions from a website but it didn't work. Then I wanted to stop it and remove.

I tried it like on this page:
[http://ubuntuforums.org/showthread.php?t=1842951](http://ubuntuforums.org/showthread.php?t=1842951)

but the /opt/utorrent-server-v3.0 folder still remains.
So I tried to remove it according to this post:
[http://ubuntuforums.org/showthread.php?t=1544097](http://ubuntuforums.org/showthread.php?t=1544097)

I deleted all files in the directory but when I say:
sudo rm /opt/utorrent-server-v3.0/

It says:

rmdir: failed to remove `/opt/utorrent-server-v3_0/': Directory not empty

What can I do to delete this?

---

### Post by Kalanac on 2012-08-09
```
sudo rm **-rf** /opt/utorrent-server-v3.0/
```

This will perform a recursive forced removal.  Because you are doing a forced removal with root privellage you will not be warned about potential problems.  DOUBLE CHECK that you are doing this to the right file location as it can be highly destructive if you get it wrong.

---

### Post by mahmut999 on 2012-08-09
Thanks. It did work.

(Anyway, why won't it :D )

---

### Post by Kalanac on 2012-08-09
If you're wanting to install stuff, it's usually always best to install it via a ppa or a repository.  Do a google search for ubuntu ppa utorrent or utorrent repository.

Adding a repository will help you keep your software up to date as well as make it much easier to install and remove programs.

Anyway, I'm glad the command cleared your problem file.  But really, rm -rf can be very bad if you use it wrong.

---

