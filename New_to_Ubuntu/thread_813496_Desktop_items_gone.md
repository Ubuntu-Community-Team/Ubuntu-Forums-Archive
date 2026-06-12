---
title: "Desktop items gone"
date: 2008-05-30
forum: New to Ubuntu
---

### Post by bgast1 on 2008-05-30
We had a power outage today, and when the power came back on and I rebooted, all I got was a blank desktop, except for the bar to launch applications. Everything else was gone. How can I get it back?

---

### Post by abhiroopb on 2008-05-30
Have you rebooted again? 
When you right click on the desktop what happens? 
When you say "all is gone" what do you mean? can you still start applications?

---

### Post by iaculallad on 2008-05-30
Hit Alt+F2 then input the code below

```
sudo debconf gnome-panel
```

then click on run and do a reboot.

---

### Post by bgast1 on 2008-05-30
I did a re-install so this became a non-issue, but I thank you all for the replies. By the way, I had already tried the reboot and right click. They didn't help.

---

### Post by iaculallad on 2008-05-30
On your terminal:

```
sudo gconftool-2 --shutdown
sudo rm -rf ~/.gconf/apps/panel
sudo pkill gnome-panel
```

---

### Post by sacback on 2008-05-31
> **bgast1 said:**
> I did a re-install so this became a non-issue, but I thank you all for the replies. By the way, I had already tried the reboot and right click. They didn't help.

I was going to say that you might want to re install your windows. That happen to me once before and I had to re install.

---

