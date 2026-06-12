---
title: "Ubuntu 12.04 boots to black screen after update."
date: 2013-04-12
forum: New to Ubuntu
---

### Post by thri11house on 2013-04-12
I just updated and restarted my computer. After the I choose Ubuntu generic in the grub menu it loads to a black screen and my monitor goes into power saving mode. I have no idea how to fix this. Can anyone guide me through this?

---

### Post by afz12 on 2013-04-12
I had the same issue and poted this a few days ago. Ubuntu 12.04 was going fine until I updated it (as recommended to improve security etc etc). Then Ubuntu just booted into a static black screen. However, switching the notebook off and selecting the advanced setting option, earlier Ubuntu 12.04 updates booted up fine.

I suspect this is a fault in Ubuntu. One reply offered some code that would remove the latest "update". However, by that time I had removed Ubuntu 12.04 and installed Ubuntu 12.10 instead. So far OK, but I suspect Ubuntu will play the same game again. In contrast, Mint has always run properly (on a second disk partition). Perhaps someone can present an explaination?

---

### Post by thri11house on 2013-04-12
I can get it to work temporarily by typing ```
radeon.modeset=0
``` at the end of the quiet splash line, but the mouse arrow flickers a lot when I'm using the computer and when I shut down and turn it on again the problem is back.

Does anyone have any idea how to fix this? It's important to have it up and running again.

Thanks!

---

### Post by r.stiltskin on 2013-04-12
Have you tried booting your previous (pre-update) kernel image?

Select "advanced options" on the Grub menu and then choose the next older Ubuntu generic (the second one listed, not recovery mode) & see if that one still works.

---

### Post by zrdc28 on 2013-04-12
Go to "**nano /etc/rc.local**" and put in "**radeon.modeset=0 **" then ctrl x and save will be a work around to get it working.[COLOR="#FF0000"][/COLOR]

---

