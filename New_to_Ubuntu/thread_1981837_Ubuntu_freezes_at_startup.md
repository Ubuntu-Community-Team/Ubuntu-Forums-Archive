---
title: "Ubuntu freezes at startup"
date: 2012-05-17
forum: New to Ubuntu
---

### Post by adfgvx on 2012-05-17
Hello everybody,

Every time I start Ubuntu 12.04, it freezes permanently right after I enter my password. Sometimes it freezes before I can type the whole password. I tried installing Gnome by pressing Ctrl-Alt-F1 at the login screen then typing

```
sudo apt-get install gnome-shell gnome-session-fallback
sudo /etc/init.d/lightdm restart
```

Now, every time I start Ubuntu, I have to press Ctrl-Alt-F1 at the login screen and enter

```
sudo /etc/init.d/lightdm restart
```

The problem is that I have to reboot my computer many times before I can get this to work. Many times it will freeze before I can enter my password, and sometimes it freezes before I can finish typing the command. Whenever it freezes, I have no choice but to force the computer to shut down by holding down the power button until it shuts off. Does anyone have any suggestions?

Thank you!

---

