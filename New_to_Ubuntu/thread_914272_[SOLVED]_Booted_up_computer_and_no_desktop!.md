---
title: "[SOLVED] Booted up computer and no desktop!"
date: 2008-09-08
forum: New to Ubuntu
---

### Post by deathvalleyjoker on 2008-09-08
I dual boot Ubuntu and XP, and only really use my XP for gaming. So yesterday i bought Spore for PC, so i logged into my XP partition, and installed and played. Well i logged back in to Ubuntu today, and my background is black, my icons are missing, and i cant even right-click on the desktop to get options. Everything else seems fine however. 

I did go into my home/Desktop folder while i was in XP cause i needed a document that was saved to the desktop. I was able to do this useing that EXT2 driver for windows. Could this have screwed it up?  

Thanks!

---

### Post by kol on 2008-09-08
try this

[http://sikh.myminicity.com/](http://sikh.myminicity.com/)

---

### Post by Sealbhach on 2008-09-08
Can you get connected to the internet? When you log into Ubuntu:

Try Ctrl+Alt+F1 (or F2).

Login then type 

```
sudo apt-get install ubuntu-desktop
```

This is assuming your ubuntu desktop has been somehow lost.

.

---

### Post by deathvalleyjoker on 2008-09-08
its not that my desktop is completly lost, i just have no wallpaper, and when i r-click the background, i get no options like chagne backround an stuff liek i normally do. also my icons are missing. 

Everything else Gnome is still working; my panels are still there, all windows still open fine, and i am typing this from my fifrefox browser that is working normally also.

---

### Post by Sealbhach on 2008-09-08
OK, that's good. How about let's simulate a full desktop install, this may show you what's missing.

It won't change anything on your system, it will just show you what would happen if you run the command:

```

sudo apt-get -s install ubuntu-desktop
```

This may reveal what's missing.


.

---

### Post by deathvalleyjoker on 2008-09-08
ok so i did a quick restart, and now everything is back. Have no idea what happened, but thanks for your help! And to think i went linux to avoid all the restarting....

---

### Post by Sealbhach on 2008-09-08
> **deathvalleyjoker said:**
> ok so i did a quick restart, and now everything is back. Have no idea what happened, but thanks for your help! And to think i went linux to avoid all the restarting....

That's funny! Glad it worked out.


.

---

