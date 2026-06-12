---
title: "Bumblebee: [ERROR]Cannot access secondary GPU, secondary X is not active."
date: 2013-03-05
forum: New to Ubuntu
---

### Post by bs_one on 2013-03-05
Hey hi,

I've installed Ubuntu a while ago already and have the problem that my graphics card is beeing used constantly and as a result my battery gets low quite fast. I've got an Optimus card (nvidia gt 630m) so i installed bumblebee to help with the powerusage, but every time i try to use bumblebee I get this error:

```
jakob@jakob-Aspire-5755G:~$ optirun -vv glxspheres
[ 4331.404129] [DEBUG]Reading file: /etc/bumblebee/bumblebee.conf
[ 4331.404828] [INFO]Configured driver: nvidia
[ 4331.405265] [DEBUG]optirun version 3.1 starting...
[ 4331.405278] [DEBUG]Active configuration:
[ 4331.405281] [DEBUG] bumblebeed config file: /etc/bumblebee/bumblebee.conf
[ 4331.405284] [DEBUG] X display: :8
[ 4331.405288] [DEBUG] LD_LIBRARY_PATH: /usr/lib/nvidia-current:/usr/lib32/nvidia-current
[ 4331.405291] [DEBUG] Socket path: /var/run/bumblebee.socket
[ 4331.405293] [DEBUG] Accel/display bridge: auto
[ 4331.405296] [DEBUG] VGL Compression: proxy
[ 4331.405313] [DEBUG]Using auto-detected bridge virtualgl
[ 4334.418019] [INFO]Response: No, secondary X is not active.

[ 4334.418086] [ERROR]Cannot access secondary GPU, secondary X is not active.

[ 4334.418100] [DEBUG]Socket closed.
[ 4334.418143] [ERROR]Aborting because fallback start is disabled.
[ 4334.418156] [DEBUG]Killing all remaining processes.
```

I tried a lot of different strategies, but somehow none of them worked :/
I kind of now my way around the shell, but I would appreciate any easy help you guys could give me :)

bs_one

---

### Post by Mark_in_Hollywood on 2013-03-06
Is this how you installed Bumblebee and is it Bumblebee ver. 3?

[https://wiki.ubuntu.com/Bumblebee](https://wiki.ubuntu.com/Bumblebee)

and from:

[http://ubuntuforums.org/showthread.php?t=2090117&page=2](http://ubuntuforums.org/showthread.php?t=2090117&page=2)

see posts starting at #11.

---

