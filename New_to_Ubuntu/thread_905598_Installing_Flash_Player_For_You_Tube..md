---
title: "Installing Flash Player For You Tube."
date: 2008-08-30
forum: New to Ubuntu
---

### Post by Breandean on 2008-08-30
Hi, I have tried twice installing flash player for you tube, no luck, once using add programs, and a flash player was installed, then from adobe, maybe I did not extract it to the right place or something...?

You Tube still says I need install the latest flash player.

---

### Post by swoll1980 on 2008-08-30
> **Breandean said:**
> Hi, I have tried twice installing flash player for you tube, no luck, once using add programs, and a flash player was installed, then from adobe, maybe I did not extract it to the right place or something...?

You Tube still says I need install the latest flash player.

Did you restart firefox? if so and it still doesn't work just take the libflashplayer.so out of it's folder, put the it (the libflashplayer.so file) on your Desktop then copy and paste this into your terminal
```

sudo mv ~/Desktop/libflashplayer.so /usr/lib/firefox-addons/plugins/libflashplayer.so
```

"sudo" gives you root privileges "~/" is a shortcut to your home directory "mv" is move. So the command says user(with root privileges) wants to move the flash plugin from his Desktop to the firefox plugin folder. This will install flash for all users on the computer

---

