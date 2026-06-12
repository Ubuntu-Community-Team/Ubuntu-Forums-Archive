---
title: "Ubuntu gnome - newbie &amp; don't windows detected"
date: 2019-05-06
forum: New to Ubuntu
---

### Post by miles87 on 2019-05-06
Hello,
I have big problem. I instal Ubuntu gnome few days ago and after install(I want to install on the same disk what windows but different particion) my computer doesn't detected windows. When I try to use commend :
```
sudo fdisk -lu
```

It was return:
```
Disk /dev/sda: 477 GiB, 512110190592 bytes, 1000215216 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: gpt
Disk identifier: 0ABE2EF2-23C2-4C4C-AF5D-29368AE122B6

Device         Start        End   Sectors   Size Type
/dev/sda1       2048    1026047   1024000   500M EFI System
/dev/sda2    1026048    1288191    262144   128M Microsoft reserved
/dev/sda3    1288192  588027903 586739712 279,8G Linux filesystem
/dev/sda4  998184960 1000212479   2027520   990M Windows recovery environment
```
When I try to recovery Windows from booting menu It's return error too (can't find some file)Can You help me can I repair It and login to partition with windows?I'm newbie so resolving step by step will be helpfull

---

### Post by TheFu on 2019-05-06
Please edit your post so _code tags_ are used, not just changing the font. See my sig below for detail steps on code tags.
Chances are that we'll need for you to install boot-repair, then run the "boot-info" script and post the URL here.  Do not ask boot-repair to do anything other than to gather information.  We need to see much more info to help.

---

### Post by Rubi1200 on 2019-05-07
Hi and welcome to the forums :-)

During installation which option did you choose, Install Alongside?

As TheFu mentioned we need more information so please follow the instructions to create a boot summary (see link in my signature). Do not attempt to repair anything, just post the summary here so we can try and help you.

Thanks.

---

### Post by TheFu on 2019-05-07
Looking at the formatted fdisk output, it appears that the Windows OS partition is gone. There is a 1GB "Recovery Environment" which might be able to reload Windows fresh.  I don't know. That's a question for Windows experts.

It isn't looking good for getting the data from that disk. I hope you have a backup of anything you cannot lose.

---

### Post by drvshrm on 2019-05-07
During installation, you need to choose Install Alongside option or just go with Manual partitioning....

---

