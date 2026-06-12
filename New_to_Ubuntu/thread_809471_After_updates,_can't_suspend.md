---
title: "After updates, can't suspend"
date: 2008-05-27
forum: New to Ubuntu
---

### Post by backflip on 2008-05-27
My Dell laptop (with Hardy Heron installed) used to suspend flawlessly until I updated Ubuntu, now it won't, I've got to force a shutdown.
Any ideas please what could have caused it and if I can undo the update that has caused the problem? :(
Thanks.

---

### Post by ercferret18 on 2008-05-27
i don't know but the same exact thing happened to me, and now i'm wondering too. it goes to suspend fine, but when i try to bring it back, the monitor won't turn back on, and none of the keys work, so i have to force shutdown. when i try to sleep in windows vista (dual booted) it works just fine.

---

### Post by iaculallad on 2008-05-27
On your terminal, try this command before suspending:

Code:

```
sudo rmmod uvcvideo
```

---

### Post by ercferret18 on 2008-05-27
it says, "ERROR: Module uvcvideo does not exist in /proc/modules

---

### Post by iaculallad on 2008-05-27
> **ercferret18 said:**
> it says, "ERROR: Module uvcvideo does not exist in /proc/modules

Try recompiling the kernel and do the restart then test your suspend. On your terminal, issue the command:

Code:

> sudo apt-get install build-essential linux-headers-`uname -r`

---

### Post by ercferret18 on 2008-05-27
um thanks, but i think i already figured it out. thanks for all your help though.

---

### Post by iaculallad on 2008-05-27
> **ercferret18 said:**
> um thanks, but i think i already figured it out. thanks for all your help though.

Try posting your solutions to the problem in the forum so other users could use it too.

---

### Post by ercferret18 on 2008-05-27
ok, i used the instructions here:

[https://help.ubuntu.com/community/NvidiaLaptopBinaryDriverSuspend]("https://help.ubuntu.com/community/NvidiaLaptopBinaryDriverSuspend")

---

