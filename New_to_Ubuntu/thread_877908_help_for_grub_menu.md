---
title: "help for grub menu"
date: 2008-08-02
forum: New to Ubuntu
---

### Post by dinsaurabh on 2008-08-02
hey everyone....cn u help me wid a problem....actually i had windows xp as well as ubuntu installed on my pc ...but due to some reasons i had to reinstall windows  and now the boot menu to select from either of the two is not appearing as i start my computer...directly windows is loading.....cn anyone tell me how to log on to ubuntu......or else how to bring back the boot menu....????

---

### Post by northern lights on 2008-08-02
check out [Recovering Ubuntu After Installing Windows]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows")

---

### Post by bumanie on 2008-08-02
You have to reinstall grub via the live cd; follow this [guide]("http://ubuntuforums.org/showthread.php?t=224351") or else download super grub disc and try that. Post back if you still need help after doing the above.

---

### Post by dinsaurabh on 2008-08-02
> **northern lights said:**
> check out [Recovering Ubuntu After Installing Windows]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows")

hey i hv done ths and the grub menu has also been loaded....but when i select ubuntu from it....it shows cannot mount from selected partition....pls reply....

---

### Post by dinsaurabh on 2008-08-02
> **bumanie said:**
> You have to reinstall grub via the live cd; follow this [guide]("http://ubuntuforums.org/showthread.php?t=224351") or else download super grub disc and try that. Post back if you still need help after doing the above.

hey i hv done ths and the grub menu has also been loaded....but when i select ubuntu from it....it shows cannot mount from selected partition....pls reply....

---

### Post by WRDN on 2008-08-02
> **dinsaurabh said:**
> hey i hv done ths and the grub menu has also been loaded....but when i select ubuntu from it....it shows cannot mount from selected partition....pls reply....

Boot recovery mode (if it works), and drop down to the root shell. Then enter the command:

```
fdisk -l
```

Please post the output here.

Also, when at the GRUB menu, press "e" when Ubuntu is highlighted, and post the contents of the line that determines what partition is booted from- it will be in the format "hd(n,n)" (n will be replaced by 2 numbers, the drive number (left) and partition (right).

---

