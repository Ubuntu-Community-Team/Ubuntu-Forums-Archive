---
title: "unstall ubuntu"
date: 2011-12-12
forum: New to Ubuntu
---

### Post by smmh on 2011-12-12
Hi friends
 
i have installed ubuntu 11.10 in my windows 7 for duel booting then i tried to uninstall it by using disk manager in windows 7 just by deleting linux swap drives and ubuntu related drives then i tried to restart my pc with windows 7 and i got an error as drive not found and iam not able to boot form windows 7 unless i installed ubuntu again using usb boot option one more thing due to this my e drive wihich was empty now shown as primary drive and iam not able to claim it please help
 
iam very new to ubuntu environment

---

### Post by MadsRC on 2011-12-12
If you've already removed the linux partition anf SWAP partitions, then, what has happened is, you've removed the part of your disk that tells you computer how to boot (GRUB).
 
What you should do now, is restore your Windows MBR. This can be done with a Windows CD. Just tell the CD to restore your windows.
 
If you don't have a windows CD or you can't restore the MBR, you can reinstall ubuntu, and delete it from within windwos and follow these steps to restore the windwos MBR: [http://www.makeuseof.com/tag/how-to-safely-uninstall-ubuntu-in-windows-dual-boot-environment/](http://www.makeuseof.com/tag/how-to-safely-uninstall-ubuntu-in-windows-dual-boot-environment/)
 
Though I'd recommend sticking to Ubuntu ;)

---

### Post by lolpenguin on 2011-12-12
Boot into a Windows restore/installation disk that corresponds with your OS and architecture (32 or 64-bit). After a few screens choose some similar to show command prompt, then run
```
fixmbr
```

---

