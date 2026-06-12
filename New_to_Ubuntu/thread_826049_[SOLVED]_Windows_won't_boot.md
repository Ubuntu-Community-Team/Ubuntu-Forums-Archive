---
title: "[SOLVED] Windows won't boot"
date: 2008-06-11
forum: New to Ubuntu
---

### Post by omi291 on 2008-06-11
Well, this actually involves SUSE linux, but i thought the issue would also apply in ubuntu. My sister decided to delete SUSE off of her machine :(, but now, when she starts up her computer, she tells me there is a grub error and windows won't boot. I'm not very linux savvy, so i would really appreciate any help.

---

### Post by Inxsible on 2008-06-11
> **omi291 said:**
> Well, this actually involves SUSE linux, but i thought the issue would also apply in ubuntu. My sister decided to delete SUSE off of her machine :(, but now, when she starts up her computer, she tells me there is a grub error and windows won't boot. I'm not very linux savvy, so i would really appreciate any help.did she simply format the suse partition?

If she did, then it probably overwrote the grub. You can do one of two things

1) Get [SuperGrubDisk]("http://www.supergrubdisk.org/") which will restore your grub

2) or you can use a XP recovery disk and do a fixmbr

---

### Post by omi291 on 2008-06-11
Yes, she did. She has a Toshiba, so would the Toshiba recovery disk to the job? Or do I acutally need a windows XP disk?

---

### Post by Inxsible on 2008-06-11
> **omi291 said:**
> Yes, she did. She has a Toshiba, so would the Toshiba recovery disk to the job? Or do I acutally need a windows XP disk?You would need a Windows XP disk and you also have to be careful not to install the XP OS again, or you WILL lose data.

Let me search for some links which will give you a detailed how to.

EDIT : Here's one: 

[http://pcsupport.about.com/od/fixtheproblem/ht/repairmbr.htm](http://pcsupport.about.com/od/fixtheproblem/ht/repairmbr.htm)

---

### Post by melrom on 2008-06-11
[http://ubuntuforums.org/showthread.php?t=818161](http://ubuntuforums.org/showthread.php?t=818161)

that might be of some help too.

---

### Post by omi291 on 2008-06-11
Never mind. I just fixed it with the supergrub cd. It was easier than i thought it would be. Thank you for the help though :)

---

