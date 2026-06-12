---
title: "No init found when booting from live cd"
date: 2011-09-10
forum: New to Ubuntu
---

### Post by shahmish on 2011-09-10
I created an Ubuntu 10.10 LiveCD using UnetBootin from Uberstudent (another linux distribution) because Windows crashed on my other computer. However, when I tried to boot from the livecd, an error message popped up, saying "no init foun. try passing init= bootarg" and a shell command line. I re-created the livecd with the same result. Any ideas how to fix this?

---

### Post by llamabr on 2011-09-10
When you very first boot into the disk, the first thing that should happen is you'll get a little text menu, and one of the options is probably 'boot from livecd' or something, so you just automatically choose it.

Instead you need to pass it an argument:

init= bootarg

at your command line.  Try that, and report back the results.  Also, why not try the ubuntu live cd?

---

### Post by Rubi1200 on 2011-09-10
If your computer allows it, try using UNetbootin to make a LiveUSB and boot from that instead.

---

