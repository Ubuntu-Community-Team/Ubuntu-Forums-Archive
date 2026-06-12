---
title: "dual boot upgrade question"
date: 2012-09-05
forum: New to Ubuntu
---

### Post by Velenjak on 2012-09-05
Hello, im using ubuntu 9.10 right now (old, I know!) and im upgrading to 12.04 lts.

ubuntu is on the first partition and windows 7 is on the second.

I read that i cannot do a simple upgrade from the 9.10 to 12.04, there will be errors so ive backed up all files on 9.10. 

Can I simply format the first slot (ubuntu) wipe it clean, and install the new ubuntu on it without harming the windows partition? thanks!

---

### Post by lincoln32 on 2012-09-05
yes
you might want to back up windows just to be safe but I have never had any issues. Just make sure you have the right partition and you should be great shape. good luck---I love 12.04:)

---

### Post by mastablasta on 2012-09-05
> **Velenjak said:**
> Can I simply format the first slot (ubuntu) wipe it clean, and install the new ubuntu on it without harming the windows partition? thanks!
 
that will be the fastest approach. 
 
otherwise you would need to upgrade to 10.04 and then to 12.04. which will take about 4 hours or so. a fresh install will take 30-45 minutes.
 
also make sure you computer is capable of running the 12.04 before doing the istall. system requirements increase a lot since 9.10 not to mention that Unity uses hardware acceleration.

---

### Post by Jakin on 2012-09-05
The way i do it, is make a Recovery Tools disc from windows, and let MBR take back control- then just plain delete the old ubuntu partition.

When you go to clean install, you get a clean Grub as well.

---

### Post by YannBuntu on 2012-09-05
> **Velenjak said:**
> Can I simply format the first slot (ubuntu) wipe it clean, and install the new ubuntu on it without harming the windows partition? thanks!

You can burn a 12.04.1 CD, boot on it, then upgrade this way: [https://help.ubuntu.com/community/UbuntuReinstallation](https://help.ubuntu.com/community/UbuntuReinstallation)

---

