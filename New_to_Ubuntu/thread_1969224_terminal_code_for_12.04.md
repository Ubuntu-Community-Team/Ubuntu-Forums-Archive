---
title: "terminal code for 12.04"
date: 2012-04-29
forum: New to Ubuntu
---

### Post by ub9876 on 2012-04-29
is there terminal code for 12.04 that would put a no ask shutdown button on the toolbars up or down..???  I have gnome, not unity.

when I shutdown it always asks for a confirm...dont want that..

and 12.04 is requiring my password to login    .... I want auto
on and when I looked at the setting ,it was on auto but still required my password.???

---

### Post by Frogs Hair on 2012-04-29
If you have auto login set it would login to the default desktop which is unity so I don't know what is happening there. Shut down from the terminal is possible , but a sudo command requires a password , so you could not create a luncher using the halt command without a password.
   
[http://theos.in/howto/howto-shutdown-reboot-ubuntu-linux-command/](http://theos.in/howto/howto-shutdown-reboot-ubuntu-linux-command/)

---

### Post by forrestcupp on 2012-04-29
There is no terminal code that will put buttons on your panel. Your best bet is to look for something similar to what you want at the [Gnome Shell Extensions web site](https://extensions.gnome.org/#). There are Shut Down extensions there, but I don't know if any of them bypass the window that asks if you're sure. Other than that, you would have to learn Gnome's api and program your own extension to do what you're talking about. It's not going to be a simple terminal command.

Also, how did you go about trying to set auto-login?

---

