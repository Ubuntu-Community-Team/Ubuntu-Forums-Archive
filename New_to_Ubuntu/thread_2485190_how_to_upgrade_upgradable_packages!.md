---
title: "how to upgrade upgradable packages!"
date: 2023-03-22
forum: New to Ubuntu
---

### Post by desatir73162 on 2023-03-22
hi there
i checked upgradable packages and there are some available but when want to upgrade them, they wont! 
more details in attached screen shot.

thanks in advanced

---

### Post by Holger_Gehrke on 2023-03-22
Which ones do you mean, the esm-apps or the other that are held back because the update is phased ? The latter are potentially dangerous (grub updates for example), so they are first only given to a random sample of systems and only given out generally when no problems come up. You can override this behaviour with the option APT::Get::Always-Include-Phased-Updates=true either in one of apt's configuration files or on the command line (sudo apt-get upgrade -o APT::Get::Always-Include-Phased-Updates=true).

The esm-apps updates are available with an Ubuntu Pro (formerly called Ubuntu Advantage) account. These are updates to packages that are generally considered to be community-maintained (so part of 'universe' or 'multiverse') which are sufficiently important that Canonical patches them. For up to five machines an Ubuntu Pro personal account is free of charge, the prices for more machines / additional support can be found at [https://ubuntu.com/pro](https://ubuntu.com/pro)

Holger

---

### Post by desatir73162 on 2023-03-23
Thanks. Lots of information in your answer. I got it

---

### Post by mIk3_08 on 2023-03-24
> **desatir73162 said:**
> Thanks. Lots of information in your answer. I got it

On how to mark this thread as solve,
Please Click the "Solve thread" link below. Regards and cheers.

---

