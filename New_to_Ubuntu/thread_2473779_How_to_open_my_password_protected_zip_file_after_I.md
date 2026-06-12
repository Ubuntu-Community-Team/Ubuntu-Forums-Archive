---
title: "How to open my password protected zip file after I entered my password"
date: 2022-04-13
forum: New to Ubuntu
---

### Post by f23948 on 2022-04-13
I can not open my password protected zip file after I entered my password in Ubuntu but I can open my password protected zip file after I entered my passwordin Linux Lite
[https://www.youtube.com/watch?v=RoiMF9bxxPc](https://www.youtube.com/watch?v=RoiMF9bxxPc)

---

### Post by TheFu on 2022-04-13
I think you need PeaZIP. Not all ZIP passwords are stored the same way. PeaZip should be in the repos.
Of course, I vaguely remember this, so it could be that peazip is specifically what you need to avoid. IDK.

Linux people tend to use compression tools that aren't ambiguous - like 7z, compress, gzip, bzip, ... you get the idea.  For anything smaller than about 250MB, I use one of the built-in compression tools to gnu-tar.  As for passwords, if I need that, it will be at the disk layer with LUKS or perhaps I'll use gpg or openssl as a filter to make encrypted.  ZIP encryption is pretty weak last time I checked.  I don't know anyone who has brute forced LUKS or gpg encrypted files. I know the FBI tried to break LUKS a few years ago and failed.

---

### Post by f23948 on 2022-04-13
Thank you!
[https://linuxhint.com/install-peazip-linux-ubuntu/](https://linuxhint.com/install-peazip-linux-ubuntu/)

---

