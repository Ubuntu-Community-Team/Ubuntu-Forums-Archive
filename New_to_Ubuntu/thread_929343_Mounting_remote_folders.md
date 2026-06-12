---
title: "Mounting remote folders"
date: 2008-09-24
forum: New to Ubuntu
---

### Post by pteri498 on 2008-09-24
At school, we're running Fedora 9 as the operating system. I have a dedicated machine at home where I would like to store my files, and I was wondering if there is a way to share, say, /home/me/homework with that computer directly.

Is there a way to mount it remotely or something like that?

Thank you.

---

### Post by ByteJuggler on 2008-09-24
There's several ways, yes, but it somewhat depends on what level of connectivity you have between the 2 machines.  (E.g, I'm expecting the school PC to possibly be behind a firewall that only allows outgoing HTTP, if even that, and on your own PC being suitably accessible from the internet.)

Personally/Ideally I would suggest you use SSHFS (e.g. mounting a remote filesystem via SSH), but this depends on you being able to SSH between the 2 boxes in at least one direction, e.g. either SSH from the school PC to your home PC or, SSH from the home PC to the school PC.  (I suspect the latter won't work, but the former might, depending on the school network/firewall setup.) 

Something else that might be an option (and even more likely to work as it works on top of HTTP), is some sort of WebDAV based sharing scheme.  See for example [this link here]("http://ubuntuforums.org/showthread.php?t=758857").  Also see [here]("http://ronaldkang.com/diary/cara-bikin-folder-webdav-di-ubuntu/") for how to share a folder wia WebDAV and [here]("http://who.hasfiles.com/support/mapping/#ubuntu") for how to mount it from a client machine.  There's also other ways to mount webDAV folders (from the command line/terminal), if you don't have similar functionality in Fedora.

---

### Post by Vivaldi Gloria on 2008-09-24
Install ssh-server on the server and sshfs in the client and then you can mount it using

```
sudo sshfs user@remote.machine:/remote.dir /where/to/mount -o allow_other
```

See my posts [here]("http://ubuntuforums.org/showthread.php?t=896474") to automount it.

---

### Post by pteri498 on 2008-09-25
I have SSH access both ways here. However, I have no root access, and I'm not sure what exactly is installed on these machines...

---

