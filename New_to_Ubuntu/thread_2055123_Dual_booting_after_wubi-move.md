---
title: "Dual booting after wubi-move"
date: 2012-09-08
forum: New to Ubuntu
---

### Post by imjooseo on 2012-09-08
Hello,

I am using Wubi to install Ubuntu 12.04 on my windows partition, then I decided to migrate the Wubi install to a partition. I followed the steps on [https://help.ubuntu.com/community/MigrateWubi](https://help.ubuntu.com/community/MigrateWubi), it was done correctly and I'm happy of the result.

The problem now is, my windows doesn't show up in boot loader - which means, I can't boot into windows. How do I resolve this? I am using Windows 7 x64 + Ubuntu 12.04.

---

### Post by anewguy on 2012-09-08
In ubuntu, try the following in a terminal window and then reboot:

sudo update-grub

---

### Post by Frogs Hair on 2012-09-08
I found this link in your link and it says that updating Grub is required for the manual method. I am not certain is this is required with the method you used. I know with my dual boot updating Grub is required so I can boot Win 7.  [https://help.ubuntu.com/community/MigrateWubiManually](https://help.ubuntu.com/community/MigrateWubiManually)

---

### Post by imjooseo on 2012-09-08
I updated grub and it detects win7 now.
Thank you for the quick replies! :KS

---

