---
title: "UEFI Boot Issue Ubuntu 14.10"
date: 2015-03-22
forum: New to Ubuntu
---

### Post by lukas24 on 2015-03-22
Hello,
I have similar issue, so I rather post it here than create a new thread.

I have new ASUS G751JY and kinda dislike win8, so I wanted dual boot win7 and ubuntu. I did it, but now I do not know how to boot ubuntu at all, and win 7 loads slowly. This is what I have done.

The computer officially supports only win8, not win7, also BIOS was first set up for UEFI, so I changed it to legacy.
I added new SSD disc to master slot and installed win 7 there.
Then I added the original disc which was in the conputer with win8, and installed there ubuntu. So my partitions look like:

sda (master SSD disc with win7)
sda1 system reserved
sda2 win7

sdb (big capacity where is ubuntu and some general storage)
sdb1 (ubuntu "/")
sdb2 (/swap)
sdb3 (bios reserved)
sdb4 (fat32 - the general storage)

After I did this, I expected to see the grub menu after restart, but win 7 just started booting. I tried to open boot menu and force ubuntu, but Bios can see only the sdb4 partition. Basicaly I do not know how to boot ubuntu now. I can also to
try set bios for UEFI and I edit the post (but I believe I just wont be able to boot anything at all).

Does someone understand what is happening to me and how to set dual boot (make grub work)? I have found a thread with similar topics, but it si closed [http://ubuntuforums.org/showthread.php?t=2210244](http://ubuntuforums.org/showthread.php?t=2210244).

Thanks in advance.

---

### Post by howefield on 2015-03-22
> **lukas24 said:**
> Hello,
I have similar issue, so I rather post it here than create a new thread.

No, you won't.

Thread moved to own thread.

---

### Post by grahammechanical on 2015-03-22
There are two issues as far as I can see.

1) If the boot system (BIOS/UEFI) is set to look for an operating system on sda then it will find Windows 7 and load that. The Windows 7 boot loader will not recognise a Linux operating system. The Ubuntu boot loader (grub) will detect a Microsoft operating system but if windows is installed after Ubuntu then grub needs to be told about the new Windows installation. We do that by loading into Ubuntu and running:

```
sudo update-grub
```

We may also need to run

```
sudo grub-install /dev/sdb
```

To reinstall Grub into sdb in your case.  We would also need to set the boot system (UEFI) to look to sdb for an operating system. Then we should get a Grub boot menu which will load either Ubuntu or Windows.

But you cannot load Ubuntu. So, you cannot do that.

2) If Ubuntu was installed in EFI mode then switching the boot system from UEFI to legacy mode will make it impossible to load Ubuntu. All operating systems (Windows and Linux) must be installed in the same boot system mode. If one is installed in EFI mode, the other must be installed in EFI mode. If one was installed in legacy mode, the other must be installed in legacy mode.

So, what is the situation with these two operating systems?

Regards.

---

