---
title: "sound loss"
date: 2008-05-09
forum: New to Ubuntu
---

### Post by amyst on 2008-05-09
I recently used alsamixer to raise the Gutsy sound volume on my dell laptop. The sound stopped working after the second or third reboot. I removed and re-installed linux-backports-modules-generic, but still no sound. I played with alsamixer but without any luck. I get the following with lspci  

[CODE]
$ lspci | grep Audio
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
[CODE]

Any idea?

---

### Post by amyst on 2008-05-10
I read 3 pages into this thread, problem solved!

[http://ubuntuforums.org/showthread.php?t=769850&highlight=sound+loss&page=3](http://ubuntuforums.org/showthread.php?t=769850&highlight=sound+loss&page=3)

---

