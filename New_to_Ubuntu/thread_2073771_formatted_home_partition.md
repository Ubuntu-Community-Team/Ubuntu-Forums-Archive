---
title: "formatted /home partition"
date: 2012-10-20
forum: New to Ubuntu
---

### Post by AlexChess on 2012-10-20
Hey guys,

so I have 2 partitions, one for / and one for /home. Now I just formatted my /home partition (using a gparted live usb), because I needed to make my / partition larger.
When I restarted, my account didn't work anymore (kind of logical since I just deleted it, I didn't think of that though).
How can I make everything work again, without reinstalling Ubuntu? It seems someone has to tell Ubuntu where the new /home drive is.

Can anyone help me with that please?

Thanks!

---

### Post by 2F4U on 2012-10-20
Since /home is no longer on a seperate partition, you could create it under the / filesystem and remove the mount point from /etc/fstab. BUT /home is more than the storage area for your personal data. All settings for the desktop environment and also application settings are stored there. So, these are all lost. Since your personal settings are anyways lost, it may be easier to install from scratch.

---

### Post by Lisiano on 2012-10-20
Boot Ubuntu in recovery mode (Hold Shift while booting and select Advanced in Grub, then select the 2nd line, it should read Recovery at the end).

Now, drop into a root shell (At the end of the list) and type in the following
```
cp -r /etc/skel /home/username
chown username:username /home/username
```
Where all instances of username are your actual username, if you don't remember it, type in the following.
```
less /etc/passwd
```
(Scroll with arrows, press q to exit)
You will find your username near the bottom
```
**lisiano**:x:1000:1000::/home/**lisiano**:/bin/bash
```
After that, type in this to make sure your changes have been written and to reboot.
```
sync
reboot
```

---

