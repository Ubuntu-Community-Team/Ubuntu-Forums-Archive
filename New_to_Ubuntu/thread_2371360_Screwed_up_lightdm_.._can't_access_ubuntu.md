---
title: "Screwed up lightdm .. can't access ubuntu"
date: 2017-09-13
forum: New to Ubuntu
---

### Post by vaskark2 on 2017-09-13
Hi. I somehow messed up my LightDM login screen. Now I can't even get into my ubuntu system. I'm greeted with a window that says:

The system is running in low-graphics mode

It gives me a list of options, like using my default graphic option but nothing seems to work. It just keeps taking me back to the above error screen.

I should note I tried some advice I found on another site by editing /etc/lightdm/lightdm.conf (which was empty) and adding:

session-greeter=unity-greeter

This was the last action taken before this all started.

Can someone help? I'm on a dual-boot laptop with Win10 / Ubuntu 17.04

Thanks. It's been awhile since I used linux and am trying to get back into it. Any help is appreciated ;)

---

### Post by again? on 2017-09-14
When you get to "The system is running in low-graphics mode", try to login to a tty console using ctrl+alt+F1
Login and edit the file with nano.
```
sudo nano /etc/lightdm/lightdm.conf
```
Use the arrow keys to navigate and delete the line you added.
Then press:
ctrl+x, followed by the y key and then Enter to save.

Reboot
```
sudo reboot
```

---

### Post by vaskark2 on 2017-09-21
Thanks!

---

