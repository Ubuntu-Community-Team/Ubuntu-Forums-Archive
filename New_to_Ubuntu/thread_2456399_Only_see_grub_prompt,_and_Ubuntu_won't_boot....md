---
title: "Only see grub prompt, and Ubuntu won't boot..."
date: 2021-01-11
forum: New to Ubuntu
---

### Post by minagawah on 2021-01-11
Hi, I need your help. I started my computer, but I only see a black screen with grub prompt. Then, I found out about the tool, Boot-Repair, so I tried running it (with recommended configurations) from Ubuntu live USB, but it looks like the tool is not able to find the original Ubuntu installation? I use EFI, and Secure Boot is disabled. I am so dead, and have no clue what to do... Please help me out.... Here is the report I got from boot-repair tool:
[https://paste.ubuntu.com/p/SbqVbsyGQS/](https://paste.ubuntu.com/p/SbqVbsyGQS/)

---

### Post by Impavidus on 2021-01-11
It appears that your system is in partition 2 of your nvme drive, but several important files and directories are missing. Boot-repair says there's no boot directory (explaining the error) nor fstab, both of which are required.

Have you got backups of all your important files on an external drive? If not, use your live disk to make those backups. Disappearing files can be quite worrying.

---

### Post by minagawah on 2021-01-11
Thanks, Impavidus. That sounds very serious... but at least I feel so relieved to hear from you for what is exactly happening. No, I have no backups. As you pointed out, I guess I will use the live usb to make a backup, probably need to wipe out the whole thing, and install Ubuntu new. Thanks a million, and I mean it.

---

### Post by yancek on 2021-01-11
Did this installation ever work?  As pointed out above, several required files to boot are missing and that would not happen on a suuccessfull installation.  Boot repair show your installation was to 
nvme0n1p2 (line 17), and there is an EFI entry for Ubuntu (line 53).  Line 129 shows the UUID for the partition on which Ubuntu was installed 
which is the same as the UUID in the grub.cfg file on the EFI partition, line 158.  Either the install was not successful or the necessary 
files were some removed/deleted.  Backup and reinstall seems the simplest solution.

---

### Post by oldfred on 2021-01-11
Did you or system do abnormal shutdown.
You can try fsck.

To see all the ext4 partitions
sudo parted -l
#From liveDVD/Flash so everything is unmounted,swap off if necessary, change example shown with partition sdb1 to your partition(s)
#e2fsck is used to check the ext2/ext3/ext4 family of file systems. -p tries fixes where response not required, Run both commands as they have different parameters.
sudo e2fsck -C0 -p -f -v /dev/sdb1
# -y auto answers yes for fixes needing response, also see man e2fsck
sudo e2fsck -f -y -v /dev/sdb1


I post generic example, in your case it should be /dev/nvme0n1p2.

---

### Post by minagawah on 2021-01-11
Gee... oldfred, that was exactly what I wanted to hear... Unfortunately, I migrated all the data, and reinstalled Ubuntu. Thank you anyways~~

---

