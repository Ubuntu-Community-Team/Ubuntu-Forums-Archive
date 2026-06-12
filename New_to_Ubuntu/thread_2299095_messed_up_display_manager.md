---
title: "messed up display manager"
date: 2015-10-15
forum: New to Ubuntu
---

### Post by rburkartjo on 2015-10-15
how can i fix. i need to change the default display manager back to /usr/sbin/lightdm it is now /usr/bin/gdm. logged in at virtual term but it would not let me change.
used cd /etc/X11      sudo gedit default-display-manager./tks

---

### Post by deadflowr on 2015-10-15
try
```
sudo dpkg-reconfigure gdm
```
If I remember right it should open a window and let you choose the display manager.
This change is only effective after a reboot, if I'm correct, or memory serves me right.

But to change it now you could stop gdm and start lightdm.
depending on which release is could be
```
sudo service gdm stop
sudo service lightdm start
```
for Ubuntu 14.04 and earlier
or
```
sudo systemctl stop gdm
sudo systemctl start lightdm
```
for 15.04 and newer.

Hope it helps

---

### Post by steeldriver on 2015-10-15
In a virtual terminal you will not be able to run a GUI editor like gedit

However, I think the usual way to reset the display manager to lightdm would be to use

```

sudo dpkg-reconfigure lightdm

```

rather than editing the default-display-manager file directly

---

### Post by rburkartjo on 2015-10-15
figured it out just logged into virtual term tpyed in sudo dpkg-reconfiure gdm and then restart lightdm

---

### Post by rburkartjo on 2015-10-15
dead  and ste tks for the speedy answers

---

