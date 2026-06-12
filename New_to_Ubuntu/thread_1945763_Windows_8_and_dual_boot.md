---
title: "Windows 8 and dual boot"
date: 2012-03-23
forum: New to Ubuntu
---

### Post by jimsing59 on 2012-03-23
When I tried to install Ubuntu on a separate partition, it says that no other OS is detected. So, I installed it anyway on the partition and now cannot boot Windows 8. I have tried Wubi, which works fine, but not happy with Linux performance with Wubi. I tried using a VM to install Linux and didn't like that option and had WiFi problems resuming Windows 8 from hibernation. Can anyone help in beginners language?

I need Ubuntu for dummies.

---

### Post by oldfred on 2012-03-23
Welcome to the forums.

Not sure how Windows 8 as you may have installed it differs from a Windows 7 install.

From Ubuntu liveCD or USB post this:

```
sudo fdisk -lu
```

Often Windows 7 vendor installs use all 4 primary MBR(msdos) partitions with BIOS. But Windows 8 is intended for UEFI and gpt installs.

---

### Post by Mark Phelps on 2012-03-24
> **jimsing59 said:**
> When I tried to install Ubuntu on a separate partition, it says that no other OS is detected. So, I installed it anyway ...

So, what made this seem like a GOOD idea?  If the installer can't see the other OS, forcing an install is ASKING for problems.

Win8 uses a different boot loader than Win7 -- and it may be that the Ubuntu installer doesn't recognize the new boot loader.

You would have done better coming here and ASKING, before you forced it.

---

