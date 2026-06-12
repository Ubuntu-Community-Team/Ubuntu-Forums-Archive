---
title: "[SOLVED] Enemy Territory 2.60 Install"
date: 2008-05-06
forum: New to Ubuntu
---

### Post by Zopiac on 2008-05-06
I got the ET install up and running, but when i try to install it it says: No write permission to /usr/local/games. I can change the directory to /home/zopiac/games and it is fine, but next it asks me for a path for the 'symbolic links'. the default here is /usr/local/bin, which, of course, doesn't work. I don't know what to do now; i cant find a suitable directory.

---

### Post by quelx on 2008-05-06
When the installer asks you for the root password click **Cancel** instead and it will runthough the install in /home/username/enemyterritory and create symlinks in /home/username/bin

That or you can install it using "sudo ./et-linux-2.60.x86.run" and it will install the game for all users in /usr/local/games

---

