---
title: "[SOLVED] Possible GRUB damage."
date: 2008-09-26
forum: New to Ubuntu
---

### Post by howitz on 2008-09-26
Ok this is how it goes.

New hdd , i install winxp just for newbies. I have Ubuntu hardy and with grub loader i choose which to use.
Now my friend infected the winxp with smart antivirus 2009 , i cannot clean it from ubuntu damn.

So i want to reformat that partition and install new winxp , is there possibility to corrupt GRUB when doing that ? 

Thanks forward.

---

### Post by Idefix82 on 2008-09-26
When you install XP it will kick out GRUB and install its own boot loader which of course ignores non MS operating systems. You will then have to reinstall GRUB which is not difficult with the Live CD.

---

### Post by Elfy on 2008-09-26
When you reinstall xp it will overwrite grub, you can easily reinstall that with either the ubuntu livecd or supergrub.

Both methods are documented here [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

### Post by howitz on 2008-09-26
Thanks guys i will try it now , so ill be updating the thread :)

---

### Post by howitz on 2008-09-26
Thanks a lot guys , SOLVED! everything went perfect :)

---

