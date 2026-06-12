---
title: "Ubuntu 18.04 login screen keeps reloading"
date: 2019-01-20
forum: New to Ubuntu
---

### Post by koerper on 2019-01-20
Brand new install from CD. Everything seemed to work ok using the live CD. After installing on HDD, I can login, but the login screen immediately reappears. Sometimes I'll get the desktop wallpaper for a second or two before it goes back to the login.

My mouse cursor is also invisible on the login screen. It becomes visible as soon as I enter my password, but disappears again when the login screen reloads. It worked fine from the live CD, but there's no login screen there. I doubt this is relevant, but... I never know.

---

### Post by CatKiller on 2019-01-20
It sounds like an X crash. Details about your hardware, particularly the graphics hardware, will give people some chance to help you.

---

### Post by koerper on 2019-01-20
I don't remember the graphics specific right now. I'll see if I can get more detailed info next time I'm able to boot to the live cd. It's an MSI motherboard, 2.6GHz 4-core AMD processor, NVidia ethernet, TP-Link wifi, and I think NVidia graphics.

---

### Post by koerper on 2019-01-20
At the login prompt, I arrowed down to highlight the option to login with a different username, manually typed in my username and password, and I was able to log in.

---

### Post by koerper on 2019-01-20
I managed to disable Nouveau (rebuilding initrd per NVidia's isntructions), and tried installing the NVidia driver, but now I'm getting this error: "unable to build the nvidia kernel module". I was able to find the log file, but I can't make heads or tails of it. Should I copy/paste it here?

---

