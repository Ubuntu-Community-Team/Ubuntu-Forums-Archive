---
title: "Not Fully Entering Suspend"
date: 2013-06-10
forum: New to Ubuntu
---

### Post by LucenNox on 2013-06-10
When trying to enter a suspend mode, to computer doesn't fully enter suspend. It shuts down most things, including, as far as I can tell, the processor, since it fan stops spinning, but the graphics card continues running, and sends a blank image to the screen. Also, whereas the main power light on the front blinks in and out on a windows suspend, it remains solidly on. 

When I hit the keyboard, that does turn on, but the computer seem to wake it up(Although I don't wait very long before moving on, since I'm skeptical of leaving my computer with an unknown level of on-ness when I know at least one fan is off). Hitting the power button definitely will wake it, and it seems to resume fine

Long story short, it  seems that the graphics card isn't entering suspend, and prevents the rest of the computer from doing so as well.


The computer is a Lenovo 3000 J series desktop
AMD 3800+
Nvidia 9800 GT
Ubuntu 12.04 LTS 64bit

---

### Post by LucenNox on 2013-06-21
I suppose it's been long enough now. Bump.

EDIT: Also, I finally let it sit, rather than waking it up a soon as the fan starts spinning faster. It wakes itself up, presumably as soon as it finishes the suspend process, so maybe it's not the graphics card after all.

Edit2:Including some logs. Sorry for the dropbox, forum kept timeing out and the files were tool large. I did a suspend about 15 minutes before I copied the logs, so sorry if the rest is just wasting space.

syslog: [https://www.dropbox.com/s/cg7tbp89g62q1tj/syslog.txt](https://www.dropbox.com/s/cg7tbp89g62q1tj/syslog.txt)
xorg.0.log: [https://www.dropbox.com/s/m93uz18e5ytjdh3/xorg0log.txt](https://www.dropbox.com/s/m93uz18e5ytjdh3/xorg0log.txt)

---

