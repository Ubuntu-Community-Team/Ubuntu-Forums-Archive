---
title: "enable blacklisted wireless network"
date: 2013-02-22
forum: New to Ubuntu
---

### Post by mr1holmes on 2013-02-22
hey, i'm using ubuntu 12.10 , few months ago i blacklisted my wireless network using following command as i wasn't using it,
```
 echo 'blacklist ath9k' | sudo tee -a /etc/modprobe.d/blacklist.conf
```
now i want to enable my wireless network , how to do that ?

---

### Post by steeldriver on 2013-02-22
You should be able to just edit the blacklist.conf file and remove (or comment out - with a #) the line you added

```
sudo nano /etc/modprobe.d/blacklist.conf
```or

```
gksudo gedit /etc/modprobe.d/blacklist.conf
```The change should take effect when you reboot

---

### Post by mr1holmes on 2013-02-22
thank you.

---

