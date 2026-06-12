---
title: "Help"
date: 2008-07-28
forum: New to Ubuntu
---

### Post by mariama on 2008-07-28
Hi!
im new in ubuntu and i dont really understand much about computers...
there's something wrong happening: when i start the pc and i select xubuntu, nothing happens...:confused: or better, it appears on my screen this:

Busybox V1.1.3 (Debian 1:1.1.3 - 5ubuntu12)
built-in-shell (ash)
enter 'help' for a list of built-in-comands

(initramfs)

i cant actually run xubuntu (neither uninstall it).
what can i do?

thank you!

---

### Post by tjwoosta on 2008-07-28
well.. i have no idea what you could have done to make this happen, but to uninstall you could always use the live cd to delete the ubuntu partition and start over

(system-administration-partition editor)


but in any case you should probably try to figure out what went wrong this time before attempting to do it again

---

### Post by fxtrem on 2008-07-28
Can you give more details? Consider reinstalling Ubuntu.

---

### Post by Diabolis on 2008-07-28
It means that while booting something went wrong. Reboot and press "esc" until you see a menu, you have to do it in the first two seconds after you turn on your pc.

You'll see a menu with only one option, press "e" to edit it. Then you'll see 3 lines of text, select the one that says "kernel". At the end of the line remove "quiet splash" and add "debug". Save the changes and reboot.

I am actually following the steps of in this thread:
[http://ubuntuforums.org/showthread.php?t=591746&page=2](http://ubuntuforums.org/showthread.php?t=591746&page=2)

Of course if you get stuck at some point or if you are not sure of what you are doing, come back we'll help you.

Note:
The title "help" doesn't says much. If you use better titles you'll get responses from people that actually are familiar with the problem. Maybe something like "can't boot" or "xubuntu hangs at boot up"

---

