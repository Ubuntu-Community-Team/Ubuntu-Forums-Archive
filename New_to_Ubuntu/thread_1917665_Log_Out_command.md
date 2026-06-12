---
title: "Log Out command"
date: 2012-01-30
forum: New to Ubuntu
---

### Post by corncob on 2012-01-30
Is there a way to log out from the terminal?  I know about the 'reboot' and 'shutdown' commands but sometimes I just want to log out or switch user.

---

### Post by josephmills on 2012-01-30
ctrl+alt+f1  that is one way another is ```
ps -ef | grep tty1
``` find /bin/login  and kill the pid # that will also log you off. hope that this helps

---

### Post by chipbuster on 2012-01-30
Are you referring to "exit"?

---

### Post by Lars Noodén on 2012-01-30
Do you mean the console, which you got to by pressing ctrl-alt-f1 or something similar?

To log out from the shell, you can type [exit](http://manpages.ubuntu.com/manpages/oneiric/en/man1/exit.1posix.html) and that will end your session.

---

### Post by corncob on 2012-01-30
Thank you all for the input. On the login screen I had changed the session from 'Ubuntu' to 'User Defined Session'.  When the screen came up it had no panels or shutdown buttons.  I could bring up the terminal with [CTR][ALT][t] and type
```
sudo reboot
```
but, since I had choosen automatic login, it didn't stop at the login screen where I had a choice of sessions but went right back into the desktop that had nothing on it.  Same thing when I hit the off switch or went to another tty and back.  
I finally got out of the loop by typing
```
cairo-dock
```
in the terminal.  This launched the dock which included a logout button on it. After that I did change it so it asks for my password.

---

