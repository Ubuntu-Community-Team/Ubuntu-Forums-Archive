---
title: "Grub does not show Windows 7 after failed Ubuntu Update"
date: 2020-03-14
forum: New to Ubuntu
---

### Post by bolzen1 on 2020-03-14
Hello,

I recently encountered a problem with my dual boot setup. I did not log into Ubuntu for a while. After recently logging in I agreed to update the System. For some reason the Windows 7 Boot option is not shown in GRUB anymore and the Device seems to be of unknown format type. It is not mounted and I cant access the Windows Installation partition in Ubunt. The data however is still available. I checked it via Windows Installation DVD (chkdsk/ dir). Ubuntu boots flawlessly but i cant boot Windows 7. I have utried to repair thee boot via "boot repiar" ([https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)). But the Tool does not offer the option "Recommended repair". I was however able to create a Boot Info Summary.

[http://paste.ubuntu.com/p/wtxzJSdRG9/](http://paste.ubuntu.com/p/wtxzJSdRG9/)

I would appreciate help for a possible solution.

Kind regards,

Marcel

---

### Post by Impavidus on 2020-03-14
First of all: both Windows 7 and Ubuntu 14.04 have reached end of life and are unsafe to use. It would be best to wipe that entire harddrive and install something supported.

It appears that your sda1 – I assume that's the Windows C partition – is damaged. Linux is unable to mount damaged Windows partitions, therefore can't detect Windows and doesn't offer to boot Windows (and if it did offer to boot Windows, it would probably fail). If there's a way to fix this, it's using a Windows repair disk or a Windows install disk. That's a Windows problem I know nothing about. After repairing Windows, you may have to repair Ubuntu, as the Windows repair will probably remove grub.

Do you have backups of all your important files? You seem able to access your Windows data partition (sda2, a.k.a. D:, I assume), so if you don't have backups, create them now.

But again: both systems have reached end of life. Best to wipe the entire drive and install something supported.

---

### Post by bolzen1 on 2020-03-14
Thanks for your answer. sda1 is indeed the Windows data partition. I can acces it by using the Windows install disk. I am going to backup important files later that day by installing the disk in a second PC with a working Windows System. I do not have important data on the linux partition, so it would be no big deal if i cant access Linux after Windows is bootable. If somebody knows a possibility to fix this issue without wiping the disk please offer some insight.

---

### Post by oldfred on 2020-03-14
Just to confirm it is not a drive issue, I would check SmartData.
In Disk and icon in upper right corner is Smartdata. It can run a variety of test, but you want to see that Disk is OK.
Use current Ubuntu live installer.

If drive is ok, then try Windows chkdsk (perhaps multiple times) on all your NTFS partitions. Chkdsk does not fix all issues on each pass. If you can backup do that before chkdsk as that may move files.

---

### Post by bolzen1 on 2020-03-15
Thanks for your reply oldfred. I ran a short test with smart data and the results are as follows "Disk is OK, 8 bad sectors". As soon as I manage to Backup the important data I am going to run chkdsk. I tried to fix the problem via WIndows Install DVD but it could not find problems automatically and the data on c:\ could be accessed with chdir, dir. Seems to be a complicated issue to fix the dualboot. I might get a SSD ( was planned anyway) and install a copy of Windows 10 on it and use the existing drive as a storage drive.

---

### Post by bolzen1 on 2020-03-15
I installed Windows 10 on a SSD and took ownership of the HDD. Everything is accessible and working. I might try to fix the HDD boot with the installation disk ("FixMBR" and "Fixboot") or just use the HDD as storage disk. Still wondering why Ubuntu cant recognize the C: partition after the update. But this solution solved most problems for me. Thanks for your help.

---

