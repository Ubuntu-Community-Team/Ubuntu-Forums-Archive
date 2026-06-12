---
title: "partition encrypted after install ubuntu"
date: 2023-04-15
forum: New to Ubuntu
---

### Post by mardibak on 2023-04-15
i have one ssd and a hard on my laptop
after install ubuntu 22.04 lts on SSD 
i cant open HARD partitions
this partitions encrypted, and i cant open any hard drive
i didn't active encryption while installing

---

### Post by TheFu on 2023-04-15
How do you know a partition is encrypted?  Which encryption tool and type of encryption do you suspect is being used?  In short, please prove what you are claiming using commands by posting both the command AND the relevant output here.  Best if it is wrapped in code tags, so it isn't too hard to read.

Let's start with this command to gather basic information:

```
lsblk -e 7 -o name,size,type,fstype,mountpoint
```

---

### Post by mardibak on 2023-04-15
i used this code and this shows me: bitlocker

---

### Post by oldfred on 2023-04-15
Bitlocker is a Windows proprietary encryption tool.

You have to turn bitlocker off in Windows if you want to use a NTFS partition with Linux.

You also have to turn off Windows fast start up as it sets hibernation flag. The Linux NTFS driver will not default mount read/write hibernated NTFS to prevent damage & file loss.

---

### Post by TheFu on 2023-04-15
> **mardibak said:**
> i used this code and this shows me: bitlocker

I vaguely remember seeing something about bitlocker support under Linux.  Don't know anything about it and I wouldn't use it myself.  Google is your friend ... and MSFT forums.

BTW, when we ask for information - like running a command, if you want more help, it is best to actually run the commands AND post the results. We can't read your mind and misinterpretation of output is extremely common.

---

