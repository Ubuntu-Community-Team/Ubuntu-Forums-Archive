---
title: "create &quot;folder synonym&quot;"
date: 2013-02-23
forum: New to Ubuntu
---

### Post by marchelloUA on 2013-02-23
Hi all, 

how do I create "folder synonym"? What I mean... Let's say I have "/host/disk/downloads/torrent" folder at bigger partition. My need is to create something like synonym in order to access it via "/home/user/torrent". My "/home/user" is at small partition, so I can't place it there.

---

### Post by The Cog on 2013-02-23
It is called a symbolic link, or symlink. It is created with a command like this, and it works for both files and folders:
```
ln -s realname linkname
ln -s /host/disk/downloads/torrent /home/user/torrent
```

---

### Post by fdrake on 2013-02-23
> **marchelloUA said:**
> "/host/disk/downloads/torrent"
both linked files/folders need to be on a unix-like filesystem . if you ar using an NTFS/FAT with a linux partition it won't work.

in the latter case you can create a launcher.

---

### Post by The Cog on 2013-02-23
I'm pretty sure it works as long as the link is on a *nix filesystem. I just tried a symlink to a FAT memory stick and that was fine.

---

