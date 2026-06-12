---
title: "Fix NetworkManager when it can't find any interfaces"
date: 2008-07-29
forum: Outdated Tutorials &amp; Tips
---

### Post by 3rdalbum on 2008-07-29
I had the problem recently where Network Manager suddenly couldn't find either of my ethernet ports or wireless. The wireless was still available if I configured it manually, but NetworkManager couldn't see anything, and nm-tool kept timing out.

This was a mystery, and then I found that my external drives weren't mounting either. CDs not mounting. Flash drives not mounting. Sound Juicer said it couldn't find any CD drives.

I tracked down the problem - HAL wasn't starting up at boot, or it was crashing at some point during boot. I discovered this through the command "lshal"; I was given a message saying that HAL wasn't running. The fix was easy:

```
gksudo gedit /etc/rc.local
```

On the line before "exit 0", put:

```
hald
```

Save your changes, close the file and reboot.

This will start HAL at some point between the main bootup sequence and the login screen appearing. If NetworkManager works, and your external drives mount automatically, then you've fixed it.

WARNING: Only modify your rc.local file if the "lshal" command tells you that HAL isn't running!

---

