---
title: "Could not create MokListRT: Volume full Boot Impossible"
date: 2023-11-08
forum: New to Ubuntu
---

### Post by jch446 on 2023-11-08
After upgrade to Ubuntu 23.10 boot impossible

error message as follows

[COLOR=#0C0D0E][FONT=-apple-system]Could not create MokListRT: Volume full Could not create MokListXRT: Volume full Could not create SbatlevelRT: Volume full Could not create MokListTrustedRT: Volume full Something has gone seriously wrong: import_mok_state() failed : volume full

[/FONT][/COLOR][COLOR=#0C0D0E][FONT=-apple-system]laptop powers off immediatetly after showing these messages......

looks like a [/FONT][/COLOR][FONT=Arial]dbx Management problem

system is laptop Asus c: volume SSD 128Gb d: volume 1TB Processor I7 Ram 16Gb


Any suggestion would be welcome.

Thanks in advance for your cooperation


[/FONT]

---

### Post by Rubi1200 on 2023-11-08
Are you dual-booting with Windows?

If yes, go to BIOS and disable Secure Boot.

Does this resolve the issue?

---

### Post by yancek on 2023-11-08
Another possibility, take a look at the site at the link below to a user with the same problem who resolved it.  I'd run sudo efibootmgr to see what that outputs.

[https://askubuntu.com/questions/1401737/couldnt-create-moklist-volume-full-grub-doesnt-start-at-all](https://askubuntu.com/questions/1401737/couldnt-create-moklist-volume-full-grub-doesnt-start-at-all)

---

### Post by MAFoElffen on 2023-11-09
Note that in the referred Link, he used a bootable LiveUSB, which you could use any bootable Linux LiveUSB, including one from Ubuntu... The user in the link used Slackware. (That distro not required.)

Summary of what he did hits on what both Rubu1200 and yancek are directing you towards...

Boot from the Ubuntu Installer LiveUSB (because your system is broken)... Do these commands ad post the results within CODE Tags:
```

sudo efibootmgr -v
lsblk -e7 -o name,size,fstype,fsused,fsuse%,model

```
What is suspected is that the ESP/EFI partition is full... When Windows installs, it feel that it will be the only OS on that computer so does not leave much room for other things when it creates that partition...  The errors indicate that that partition is full. This may be caused by old entries that are no longer needed. 

What may fix it is to remove those old unneeded entries.

---

