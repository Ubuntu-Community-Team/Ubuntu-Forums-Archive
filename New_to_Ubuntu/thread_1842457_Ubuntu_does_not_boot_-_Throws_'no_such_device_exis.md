---
title: "Ubuntu does not boot - Throws 'no such device exists.' error"
date: 2011-09-11
forum: New to Ubuntu
---

### Post by learncode on 2011-09-11
Hello:

I installed ubuntu [dual boot with windowsXP] using Wubi a week ago. Today as I started the 

```
NTFS5: error no such device: ubuntu/disks/root.disk.
NTFS5: error no such device: ubuntu/install/boot/grub/grub.cfg.
```

Which directly takes me to, 
```
GNU GRUB version 1.98 - 1ubuntu12
```

I have seen [1]("http://ubuntuforums.org/showthread.php?t=1639198") and [2]("http://ubuntuforums.org/showthread.php?t=1689388") but neither helped me solve the problem.

Investigation I did:
- Default installation Of Windows: C:\
- Ubuntu Installation Inside Windows [Under drive C]
- wubildr: C:\wubildr and wubildr.mbr: C:\wubildr.mbr. And these also existin the C:\ubuntu\winboot directory
- Under C:\ubuntu\disks I do find root.disk and swap.disk. 
- Along with the files mentioned above under [C:\ubuntu\disks] there's another folder boot, which has grub under it and that doesn't have anything. I gave this just for additional details so it might help you.

What should I be doing now? re-installing or what else?

Thank you.

---

### Post by habba babba on 2011-09-11
i sort of had this problem. ubuntu has a check option that you can choose by pressing tab at the prompting screen with the simple white text. type in the one that says 'check' (may be diff. depending  on your comp) then press enter. it'll run a check and tell you if the version of linux is 100% intact or not (basically.)

---

### Post by learncode on 2011-09-11
Thank you for the input a combination of things worked for me, I did what you mentioned and I selected the recovery option, there instead of upgrading grub I did select the console and ran few commands specified [here]("http://ubuntuforums.org/showthread.php?t=1639198") in the permanent fix section and it worked.

---

