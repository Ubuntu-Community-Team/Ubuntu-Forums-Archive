---
title: "cursor missing"
date: 2015-09-02
forum: New to Ubuntu
---

### Post by mrperdue on 2015-09-02
I am running the latest release of Ubuntu. After a couple of weeks of operating the Cursor is not visible on the screen. I am able to  log off and back on by using key functions but unfamiliar enough to do any thing else. What can I do to correct this.

---

### Post by dino99 on 2015-09-03
a few tweaks can be made:
- swith to an other theme, to check if its a related issue
- purge/downgrade  the non genuine packages
- clean the system: clean/autoclean/autoremove/gtkorphan
- reinitialize compiz/metacity/gnome-shell/.... (adapt to to DE)
- reconfigure the system (sudo dpkg --configure -a)

---

### Post by CantankRus on 2015-09-03
Is it visible in the guest account?

---

### Post by chemist931 on 2015-09-07
This fixed it for me:
```
sudo service lightdm restart
```
You will have to do this every time you start your computer, and unfortunately I don't have a more permanent fix.

---

### Post by col48 on 2015-09-07
re post #4

Could the service call be put in the list of startup tasks, perhaps after a brief pause?  Not a brilliant way forward, but...

---

