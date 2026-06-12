---
title: "Ubuntu 15.04 no longer shows Windows boot option"
date: 2015-04-30
forum: New to Ubuntu
---

### Post by E.Mayler on 2015-04-30
I am a novice Ubuntu user . After upgrading to Ubuntu 15.04 from 14.10 , I no longer get the option to boot Windows .  How do I edit grub to allow this function please ?

---

### Post by grahammechanical on 2015-04-30
Load into Ubuntu and open the terminal and run this command

```
sudo update-grub
```

Watch the printout. See, if it detects a Windows boot loader.

The upgrade would have brought in a newer Linux kernel and that would have triggered the update-grub command. And that in turn should have detected any Windows boot loader that was anywhere on the disk.

Do you have Windows and Ubuntu on separate disk drives? Was the Windows drive disconnected during the upgrade of Ubuntu. That sort of thing would cause this problem.

Regards.

---

