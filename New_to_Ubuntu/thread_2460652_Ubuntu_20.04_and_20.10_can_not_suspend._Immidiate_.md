---
title: "Ubuntu 20.04 and 20.10 can not suspend. Immidiate wakeup. Lenovo IdeaPad 5."
date: 2021-04-15
forum: New to Ubuntu
---

### Post by 0x54 on 2021-04-15
My Ubuntu installation is not able to suspend. The issue has persisted throughout both versions mentioned in the title. 
I have had rare cases where it was able to suspend but right now it never works.
When the system suspends it immediately wakes up again.
I have disabled all wakeup devices except for the lid switch.

In the logs I can see this:
```
manager: sleep: wake requested (sleeping: yes  enabled: yes)
```
From the NetworkManager which appears after an unsuccessful suspend attempt aswell as:

```
Failed to set mode: Blocked through rfkill (0x12)
```
from bluetoothd.

Another issue is that after a failed suspend, there is a high load on core 0 of ~90% and overall high lag.

---

### Post by blackbird34 on 2021-04-20
Hi. I had that problem for months. I read lots of forum posts about my model (MSI Modern 14 with a Ryzen 5 4500) and other Ryzen laptops including the Ideapad 5 and I tried everything under the sun, struggled for a while, spent weeks using hibernation instead of sleep. 

In the end what solved it was a BIOS (UEFI) update. Are you on the latest BIOS?

---

### Post by 0x54 on 2021-05-01
Apologies for the late response. 
For some reason I didn't get a Notification.

I just checked in windows an I seem to have the latest BIOS.

---

