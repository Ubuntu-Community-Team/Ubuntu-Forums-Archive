---
title: "LUBUNTU How to compress totally an BTRFS partition ?"
date: 2020-07-31
forum: New to Ubuntu
---

### Post by aug7744 on 2020-07-31
I have installed Lubuntu 20.04 in an BTRFS partition where the disk is MBR being 4 primary partitions 1 Start, 2 windows, 3 Lubuntu and 4 ntfs. I had installed using / to disk partition utility of installer. How to compress the BTRFS partition and choice an compression mode (low or high compression) and also automatic compression ? I understand that has files that not will be compressed. I not see the time to finally replace windows with Linux. I had that have tested that system much time before !

---

### Post by The Cog on 2020-07-31
The option to compress is an option that is set when the disk is mounted. For the / partition, that is of course at boot time. The file that defines the boot options is /etc/fstab. You can add compress to the list of options (comma separated) on the appropriate line. Then reboot for the options to take effect.

You cannot **force** btrfs to compress. The compress option tells btrfs to *consider* compressing files, and it will choose based on the file contents. For instance, it won't try to compress files that are already compressed such as music and videos. The command "man mount" will give more details about the options.

---

### Post by aug7744 on 2020-07-31
I will try to configure.
Thanks for reply.

---

