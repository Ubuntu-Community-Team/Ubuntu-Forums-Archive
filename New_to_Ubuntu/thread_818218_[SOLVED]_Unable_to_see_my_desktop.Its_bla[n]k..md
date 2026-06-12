---
title: "[SOLVED] Unable to see my desktop.Its bla[n]k."
date: 2008-06-04
forum: New to Ubuntu
---

### Post by rraj.be on 2008-06-04
when i booted my computer this evening my desktop was completely black and blank.

No background, no icons.

what should i do to test where the fault is.

Is there any solution.

---

### Post by bumanie on 2008-06-04
Try pushing ctrl+alt+F1 and see if that takes you to console mode. If so answer username, password and then type > sudo apt-get --reinstall ubuntu-desktop followed by enter. The sudo apt-get update --> enter. Then push ctrl+alt+F7 and see if that works. If not, try booting in via safe graphics.

---

### Post by prshah on 2008-06-04
> **rraj.be said:**
> when i booted my computer this evening my desktop was completely black and blank.
No background, no icons.
what should i do to test where the fault is.
Is there any solution.

Does a restart of GDM give you back your desktop?

To restart GDM, switch to Ctrl+Alt+F1, login, give the command
```
sudo /etc/init.d/gdm restart
```

, then when you get the [OK], switch back with Ctrl_Alt_F7.

If it doesn't give you back your desktop, but you can switch to a virtual terminal (F1) then use lynx (text only browser) and paste your /var/log/messages file _as an attachment_.

---

### Post by rraj.be on 2008-06-04
Reinstalling is a big issue for me because it takes 5 minuites for my internet to download 1MiB.

But i solved it.

I ran check disk.

It got me 8 errors and after fixing it, its working fine.

---

### Post by rraj.be on 2008-06-04
I tried to restart my GDM.

But there is no use.

It just replied that there was a fatal error and your x-server had failed.

restart your gdm after getting solved.

then it took me to the console.

Now i solved this problem by check disk.

---

