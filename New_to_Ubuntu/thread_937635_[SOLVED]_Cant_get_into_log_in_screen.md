---
title: "[SOLVED] Cant get into log in screen"
date: 2008-10-04
forum: New to Ubuntu
---

### Post by phantomgunex on 2008-10-04
Hi! My ubuntu com just crashed  so i reinstalled it(obvious ubuntu ROCKS!:o:D). A day after i reinstalled ubuntu, all hell came loose!!! After the system start up screen(the screen with the bar moving left and right), i just got this black screen with only the busy cursor in the middle! Someone help me plz!!!](*,)

---

### Post by Lord DarkPat on 2008-10-04
> **phantomgunex said:**
> Hi! My ubuntu com just crashed  so i reinstalled it(obvious ubuntu ROCKS!:o:D). A day after i reinstalled ubuntu, all hell came loose!!! After the system start up screen(the screen with the bar moving left and right), i just got this black screen with only the busy cursor in the middle! Someone help me plz!!!](*,)

Boot into recovery mode from GRUB, and run "apt-get install kdm" (without quotes) This installs the KDE Display Manager.

---

### Post by phantomgunex on 2008-10-04
> **Lord DarkPat said:**
> Boot into recovery mode from GRUB, and run "apt-get install kdm" (without quotes) This installs the KDE Display Manager.

tried it but when i dropped into the root shell and enter the command, i got errors like: the following packages are not going to be installed kde:Depends: kde-core 9>=5:47) but it is going to be installed.
nevermind i will just reinstall it as it is only 2 day old... zzzzzzz

---

