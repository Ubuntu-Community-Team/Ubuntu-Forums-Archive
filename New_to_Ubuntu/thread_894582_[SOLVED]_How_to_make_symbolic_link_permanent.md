---
title: "[SOLVED] How to make symbolic link permanent"
date: 2008-08-19
forum: New to Ubuntu
---

### Post by Bob Heap on 2008-08-19
[FONT="Courier New"][/FONT]****
[COLOR="Red"]SOLVED[/COLOR]
Hi Guys. I have a symbolic link to my modem e.g.

sudo ln -s /dev/536ep0 /dev/ttyS5

this works fine, no problem.However I have to re-enter this every time I reboot as it disappears.
Is there a way of making the link permanent?

---

### Post by fahadsadah on 2008-08-19
Udev rules are the way to do this.

[http://reactivated.net/writing_udev_rules.html](http://reactivated.net/writing_udev_rules.html) has an explanation.

Do you know the kernel name for /dev/536ep0?

---

### Post by fahadsadah on 2008-08-19
Sorry, no need. The udev rule is:```
KERNEL=="536ep0" SYMLINK="ttyS5"
```

Save this to the file /etc/udev/rules.d/10-local.rules

The bash redirection for this is ```
echo 'KERNEL=="536ep0" SYMLINK="ttyS5"' | sudo tee -a /etc/udev/rules.d/10-local.rules
```

Precedent: [http://ubuntuforums.org/showthread.php?t=476460](http://ubuntuforums.org/showthread.php?t=476460)

---

### Post by decoherence on 2008-08-19
fahadsadah's suggestion is correct. the reason you do this with udev rules is because the /dev directory is dynamically created by udev, hence why the symlink doesn't survive a reboot. under normal circumstances, symlinks are permanent.

---

### Post by fahadsadah on 2008-08-21
Bop Heap: Rather than writing SOLVED at the top of your thread in red, please go to Thread Tools at the top, and mark this thread solved.

---

