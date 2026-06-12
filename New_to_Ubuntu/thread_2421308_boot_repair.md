---
title: "boot repair"
date: 2019-06-19
forum: New to Ubuntu
---

### Post by cid-paulo on 2019-06-19
I have dual boot with windows 10 and Ubuntu 19.04, on the boot screen it presents the error Minimum edition similar to BASH, I have grub 2.02, I run the boot repair that did not correct the problem but generated the following report

[http://paste.ubuntu.com/p/gvT92qYTND/](http://paste.ubuntu.com/p/gvT92qYTND/)

---

### Post by oldfred on 2019-06-19
You show no Linux partition.
Your UEFI boot wants to boot from this partition which does not exist?
      >  search.fs_uuid a3615935-f582-4313-8d00-ab3e6bf88f1e root hd0,gpt5  



If hd0 is sda, your Windows takes up entire drive. If really sdb, same issue as NTFS partition takes up entire drive.

Your Windows fast start up is on, did Windows do a major update? And turn fast start up & Secure boot back on?

Do you have any backups of your Ubuntu?
Do you have partition table info from before where it still had ext4 partition for Ubuntu?

You can try testdisk and see what it says, it may show old ext4 partition. 
But you may need to just reinstall & restore from your backups.
       [http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)
[http://www.cgsecurity.org/wiki/Menu_Analyse](http://www.cgsecurity.org/wiki/Menu_Analyse)

---

