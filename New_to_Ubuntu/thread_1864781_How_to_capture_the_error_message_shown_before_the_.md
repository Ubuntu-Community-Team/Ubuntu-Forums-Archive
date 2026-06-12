---
title: "How to capture the error message shown before the log in screen"
date: 2011-10-19
forum: New to Ubuntu
---

### Post by meadhikari on 2011-10-19
I get many message's before the login screen comes. IS there a way to save that message so that I could share it to the community and find some solution to its.

My computer boots fine but after the grub and before the log in screen some unusual message (not seen before) appears, how could i capture that?

---

### Post by ubudog on 2011-10-19
Hey there, those messages are probably just start up messages (which is normal), and nothing to worry about.

But, to view recent system messages, type:
```
dmesg
```

into a terminal.

Regards,
- ubudog

---

### Post by meadhikari on 2011-10-19
Thanks
and these are the message, they never used to appear before
Are they normal?
```

[    0.685239] EXT3-fs (sda1): error: couldn't mount because of unsupported optional features (240)
[    0.685563] EXT2-fs (sda1): error: couldn't mount because of unsupported optional features (240)
[    0.714605] EXT4-fs (sda1): mounted filesystem with ordered data mode. Opts: (null)
[    0.714725] VFS: Mounted root (ext4 filesystem) readonly on device 8:1.
[    0.746476] devtmpfs: mounted
[    0.746552] Freeing unused kernel memory: 688k freed
[    0.746945] Write protecting the kernel text: 4932k
[    0.747028] Write protecting the kernel read-only data: 1980k
[   16.958986] <30>udevd[112]: starting version 173
[   17.031974] intel_rng: FWH not detected
[    0.714725] VFS: Mounted root (ext4 filesystem) readonly on device 8:1.
[    0.746476] devtmpfs: mounted
[    0.746552] Freeing unused kernel memory: 688k freed
[    0.746945] Write protecting the kernel text: 4932k
[    0.747028] Write protecting the kernel read-only data: 1980k


```

---

### Post by ubudog on 2011-10-19
Yep, looks normal from here.

---

### Post by meadhikari on 2011-10-19
It pauses around the above message for like 20 to 30 second at every startup and I really hate that.

Any way to remove this and make the boot up process faster.

Are the error shown in the first few message perfectly normal

Thanks for your time.

---

