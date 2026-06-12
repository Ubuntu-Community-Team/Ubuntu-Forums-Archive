---
title: "Graphics issue (3870 ATI)"
date: 2008-04-24
forum: New to Ubuntu
---

### Post by Shnooky on 2008-04-24
I am having a problem obtaining graphics drivers for my 3870 ati card.  I have updated everything in terminal and have installed envy and used it.
The problem is that my onboard (nvidia) is the only one displayed in the "restricted driver management" and envy didnt work becuase on boot up it still says i have to to use it in low graphics mode...

I am lost at what to do, all help is appreciated
thx
-shnooky

---

### Post by overdrank on 2008-04-24
> **Shnooky said:**
> I am having a problem obtaining graphics drivers for my 3870 ati card.  I have updated everything in terminal and have installed envy and used it.
The problem is that my onboard (nvidia) is the only one displayed in the "restricted driver management" and envy didnt work becuase on boot up it still says i have to to use it in low graphics mode...

I am lost at what to do, all help is appreciated
thx
-shnooky

Hi and you still may have to configure you xorg even after using envy. You can try this command on the terminal ```
sudo dpkg-reconfigure -phigh xserver-xorg
``` Then you can use this command to view what driver is being used ```
cat /etc/X11/xorg.conf
```

---

### Post by Shnooky on 2008-04-24
how can i tell if it took affect

---

