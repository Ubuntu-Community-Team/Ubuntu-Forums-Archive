---
title: "Error message on Boot Up"
date: 2012-02-22
forum: New to Ubuntu
---

### Post by mihalaj on 2012-02-22
What does the error message:

"fsck from utile-linux-ng 2.17.12
/dev/sda1: clean, 89063/29466624 files, 2267881/117854720 blocks" on boot up mean?

If you know, how can it be fixed?  The server freezes at this message.

Thanks for any and all help!

---

### Post by roelforg on 2012-02-22
It's no error.

Just fsck reporting you HD is OK.

---

### Post by mihalaj on 2012-02-22
Thank you, but how do I get the server to go beyond that message.  It never did tha until recently.  Up until about a week ago, the Ubuntu server was operating fine.  Now it freezes on the posted message.

---

### Post by roelforg on 2012-02-22
> **mihalaj said:**
> Thank you, but how do I get the server to go beyond that message.  It never did tha until recently.  Up until about a week ago, the Ubuntu server was operating fine.  Now it freezes on the posted message.
Every so many mounts (=boots) fsck will autocheck the HD; appears to hang, it doesn't, it just takes time.
Give it about 30 min, should be enough.

---

### Post by mihalaj on 2012-02-23
After 18 hours now, the boot up screen is still on hold at the original message.  Any ideas as to what the problem would be?

---

### Post by d4m1r on 2012-02-23
If the server hangs when the disk is being checked, the partition could very well be cooked or even the harddrive could be experiencing hardware failure...I'd make a backup of your data if you can access it for just in case.

---

