---
title: "Grub OK, but then &quot;ALERT! /dev/diskby uuid/&quot;...&quot;does not exist&quot;"
date: 2015-11-24
forum: New to Ubuntu
---

### Post by soundgeek on 2015-11-24
Lubuntu 14.04. was working fine, but suddenly I found Linux would not boot.

Selecting the debug options from the GRUB menu does not work either. A live CD boots, but I don't know what to do next.

WinXP boots fine, but required disk checks.

How do I fix this? Is there a repair utility?

---

### Post by oldfred on 2015-11-24
Very old PC with BIOS boot limit and large / (root)? And update just happened to move kernel further into / ?
If so it can be the very old bug where BIOS cannot boot from files beyond 137GB on a drive. Or you have BIOS in old IDE mode and it should be AHCI. But XP does not work with AHCI.

       Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

---

### Post by soundgeek on 2015-11-25
> **oldfred said:**
> Very old PC with BIOS boot limit and large / (root)? And update just happened to move kernel further into / ?
If so it can be the very old bug where BIOS cannot boot from files beyond 137GB on a drive. Or you have BIOS in old IDE mode and it should be AHCI. But XP does not work with AHCI.

       Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

It is quite an old machine. I'm trying to revitalise it with Lubuntu. It was going well until now.

I'm not familiar with different BIOS "modes". I haven't changed anything in the BIOS.

Thanks for the Boot-info link **oldfred**. I followed the instructions for using an installation disk, resulting in this [report]("http://paste.ubuntu.com/13504048").

---

### Post by oldfred on 2015-11-25
If real old it may only have IDE, not the ACHI.

Did system boot ok before? Since sdb1 is smaller it is not the large drive issue.
Did you boot from sdb? Or only from sda? Have you tried both again?
Or is BIOS, not allow that. Very old systems had jumpers on hard drives to determine boot drive. Somewhat newer IDE systems had cable select with a newer IDE cable and BIOS could select sdb drive for boot.

Script seems to be reporting something on all your FAT32 partitions. And with XP in FAT32, not NTFS, then it is a very old system.
I might run chkdsk on all your FAT32 partitions, but that is unrelated.

---

### Post by soundgeek on 2015-12-01
> **oldfred said:**
> If real old it may only have IDE, not the ACHI.
It has two IDE disks. I had windows on the master disk originally, using some partitions on the other disk. Then I installed Lubuntu on the other disk, with GRUB allowing me to boot either system.

> 
Did system boot ok before? Since sdb1 is smaller it is not the large drive issue.


I boot the master disk & then GRUB presumably redirects to Linux on the slave disk or the Win XP system on the master disk if I choose that. I had been using linux on a regular basis. So the master disk boots & GRUB comes up ok, but if I select Linux, I get the alert message. If I select windows, it boots fine & allows me access to partitions on the slave disk.

> 
Did you boot from sdb? Or only from sda? Have you tried both again?
Or is BIOS, not allow that. Very old systems had jumpers on hard drives to determine boot drive. Somewhat newer IDE systems had cable select with a newer IDE cable and BIOS could select sdb drive for boot.


The jumpers on the drives determine master and slave & so the master is booted.

> 
Script seems to be reporting something on all your FAT32 partitions. And with XP in FAT32, not NTFS, then it is a very old system.
I might run chkdsk on all your FAT32 partitions, but that is unrelated.

When I couldn't boot Linux, I booted WinXP and that forced me to run a check on all drives.

Maybe I hadn't shut down properly from Linux?

Is there something I can run from a boot DVD that will check/repair the Linux partitions?

Thanks for your help!

---

### Post by yancek on 2015-12-01
You could take a look at the link below which gives examples of using the fsck command to run a filesystem check on Linux partitions.  Curious that all your xp partitions are FAT32 which is definitely not  the standard.  All the boot sector errors reported in boot repair are on your FAT32 partitions.  Not sure what that means.

[http://www.thegeekstuff.com/2012/08/fsck-command-examples/](http://www.thegeekstuff.com/2012/08/fsck-command-examples/)

---

### Post by oldfred on 2015-12-01
These are the fsck commands I suggest:
 #From liveDVD/Flash so everything is unmounted,swap off if necessary, change example shown with partition sdb1 to your partition(s)
#e2fsck is used to check the ext2/ext3/ext4 family of file systems. -p trys fixes where response not required
sudo e2fsck -C0 -p -f -v /dev/sdb1
#if errors: -y auto answers yes for fixes needing response, also see man e2fsck
sudo e2fsck -f -y -v /dev/sdb1

But if drive is that old, we also have to worry about drive.
You can use Disks in newer versions of Ubuntu or Disk Utility in older versions. That also has Smart Status. In newer version it is in gear icon in upper right. I do not know all the detail tests or what results mean on those drive tests. But if drive shows ok then you are ok, but if not good then time for new drive. Drives may be so old they do not support Smart Status.
And if system is that old, probably a new system. Even a used several year old system would be a lot faster/better.

---

### Post by VMC on 2015-12-01
I'm curious , from a terminal,  what does the command below show?```
ls -l /dev/disk/by-uuid/
```

---

### Post by soundgeek on 2015-12-05
> **yancek said:**
> You could take a look at the link below which gives examples of using the fsck command to run a filesystem check on Linux partitions.  Curious that all your xp partitions are FAT32 which is definitely not  the standard.  All the boot sector errors reported in boot repair are on your FAT32 partitions.  Not sure what that means.

[http://www.thegeekstuff.com/2012/08/fsck-command-examples/](http://www.thegeekstuff.com/2012/08/fsck-command-examples/)

I'll try this.

No, I don't know what the boot sector errors mean either. Linux was accessing all the logical drives fine. Win XP still accesses the FAT32 logical drives fine.

I booted an installation disk & I tried these commands and the file systems in the system & home directories come up clean.

I can mount the system partition and browse it.

Before the "ALERT!" message, it mentions common errors. It says to "cat /proc/cmdline" and check "rootdelay=" and "root=".

I looked in /proc but it seems empty. What needs to be in here?

I've found a page of advice which seems to describe the problem I have: [ALERT!]("http://www.dedoimedo.com/computers/ubuntu-initrd-bug.html")

I booted the installation disk & used cd in term to get to /media/lubuntu/3d1...
I could see that initrd.img-3.16.0-53-generic (Gzip archive) is only 5.4 MiB 11/17/2015 09:58, whereas earlier initrd.img files are all 18.2 MiB. Permissions: lrwxrwxrwx.
initrd.img-3.16.0-49-generic 09/15/2015 11:36 was probably the last file which worked ok (initrd.img.old).

I deleted the current initrd.img and copied initrd.img.old to initrd.img.

The permissions were wrong so I tried to use chmod to correct them. I got rwxrwxrwx, not lrwxrwxrwx. I don't know what the initial "l" is. File manager does not seem to recognise this as an archive image file in the way it did for the most recent initrd.img file.

I tried re-booting, but with the same ALERT! result.

I feel the problem is the failure to launch ramdisk due to a corrupt (small) initrd.img but don't know how to fix this.

Any ideas?

---

### Post by yancek on 2015-12-15
> I don't know what the initial "l" is.

It means it is a link to the actual file.

---

### Post by oldfred on 2015-12-15
The initrd.img and vmlinuz in / are a links to the most current kernel. And the .old is to the previous kernel. The l at beginning of permissions shows it is just a link. It should have just a very small file size. Those should be in / not in /boot. Example you link to is very old 2. kernel, do not know if links were in /boot back then?

Do not change permissions or ownership on system files. That can totally corrupt a system. Many have to be owned by root, but some have other systems ownership. And whatever permissions they have are correct when booting. View from another system may not be exactly the same.

---

### Post by soundgeek on 2015-12-16
Thanks yanek.

Is there a way to just edit the link to have it point at the old file instead of the current corrupt one?

Ubuntu does seem rather fragile. I don't know how it got into this state, what state it is really in or how to fix it.

The disk drives are physically fine & all the file systems check out fine.

I've given up & re-installed. So it is fixed, but not "solved";  I don't know how to stop it doing it again.

---

### Post by soundgeek on 2016-02-24
I re-installed Linux from the Live disk & this fixed the problem, whatever it was.

---

### Post by soundgeek on 2016-02-24
Thank you yancek :)

---

