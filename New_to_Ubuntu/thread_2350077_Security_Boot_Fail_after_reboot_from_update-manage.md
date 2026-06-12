---
title: "Security Boot Fail after reboot from update-manager"
date: 2017-01-21
forum: New to Ubuntu
---

### Post by clowncombat on 2017-01-21
Hello lovely Ubuntu Community!

I am relatively new to ubuntu. I successfully installed it about 20 days ago, and it was quite an exciting and fun experience so far.

**My Problem:**
Today I run the update-manager, which installed some updates (about 92mb or so), and then asked to reboot the system. 
I entered my sudo-pw, and then my laptop said: "Security Boot Fail".

I have UEFI and secure boot enabled. I also created / configured an EFI File Boot before, which worked until now.

[B]Helpful Information:
[/B]Ubuntu Version: 16.04
Information about my pc:
Laptop - Acer Aspire VN7-572G-709S

Also: 
I changed the boot-order before, with the efibootmgr. Could it be possible, that this order was reset by the update-manager? (If yes, this will be ugly for me in the future..)


I hope you can help me with this problem :S

Many thanks inbefore,
ClownCombat

---

### Post by clowncombat on 2017-01-21
**Update:**
I once again selected an EFI-File to boot (grubx64 or so), saved and exit in the boot menu and then it started normally. (yaaay :D)
So, the problem seems to be solved, but I know nothing about the cause.

---

### Post by oldrocker99 on 2017-01-21
If your problem is solved, please mark this thread as [SOLVED] to help others. Thanks.

---

