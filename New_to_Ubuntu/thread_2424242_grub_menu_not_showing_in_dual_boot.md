---
title: "grub menu not showing in dual boot"
date: 2019-08-05
forum: New to Ubuntu
---

### Post by shivamgoel050 on 2019-08-05
i installed my ubuntu on ahci mode and my windows pre-installed on Raid-On mode. it worked fine for a month and then one day when i changed to ahci mode in bios setup and tried getting into ubuntu the grub menu did not show up and it just kept restarting on dell loading screen and when i change to raid on mode again grub menu did not show up and boot straight into windows.
i dont know what went wrong.


Now i dont see my ubuntu in bios setup boot sequence also.


after research i think its not detecting hard drive as in diagnostics it says hard drive not installed.

windows working fine. what can i do?

boot-repair detalis [http://paste.ubuntu.com/p/SM7DyxNRqq/](http://paste.ubuntu.com/p/SM7DyxNRqq/)

---

### Post by oldfred on 2019-08-05
Script is not good about showing details on NVMe drives, but should show it in list of drives & UUIDs.
Not seen anywhere?
Usually Ubuntu will see RAID, but grub will not install or install correctly to RAID drives unless using Server installer.

I know many users need UEFI updates & SSD firmware updates to have system worked. Not sure why if it worked before why now it stopped working.

---

