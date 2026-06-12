---
title: "Rename Root Logical Volume group?"
date: 2013-07-17
forum: New to Ubuntu
---

### Post by isac630728 on 2013-07-17
Hello,

I'm running Ubuntu 12.04. I need to rename my root logical volume group and it's bootmanager/fstab accordingly.

Here is the output: I need to change the HP-TEST001 to PRODGROUP01. Please advice me.


root@PROD-02:/home# vgdisplay
  --- Volume group ---
  VG Name               HP-TEST001
  System ID
  Format                lvm2
  Metadata Areas        1
  Metadata Sequence No  3
  VG Access             read/write
  VG Status             resizable
  MAX LV                0
  Cur LV                2
  Open LV               2
  Max PV                0
  Cur PV                1
  Act PV                1
  VG Size               9.76 GiB
  PE Size               4.00 MiB
  Total PE              2498
  Alloc PE / Size       2498 / 9.76 GiB
  Free  PE / Size       0 / 0
  VG UUID               vMIkzy-BCSa-bSHb-zt84-2xZ4-Xidm-zf46xB


root@PROD-02:/home# cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/mapper/HP--TEST001-root /               ext4    errors=remount-ro 0       1
# /boot was on /dev/sda1 during installation
UUID=29b6596c-j4r2-47db-9890-c654c9ca4c46 /boot           ext2    defaults        0       2
/dev/mapper/HP--TEST001-swap_1 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0


root@PROD-02:~# df -h
Filesystem                        Size  Used Avail Use% Mounted on
/dev/mapper/HP--TEST001-root  9.3G  1.5G  7.4G  17% /
udev                              2.0G  4.0K  2.0G   1% /dev
tmpfs                             791M  268K  791M   1% /run
none                              5.0M     0  5.0M   0% /run/lock
none                              2.0G     0  2.0G   0% /run/shm
/dev/sda1                         228M   27M  189M  13% /boot

---

### Post by isac630728 on 2013-07-17
Can someone please help? Anybody?

---

### Post by capscrew on 2013-07-18
I am surprised you couldn't google for the answer.  The actual command is: *lvrname*.  The google keywords to find help are: **rename LV lvm2**

I'm not going to tell you to do this, only that I have done this on storage volumes.  My first inclination is tell you to leave it alone.  But if you insist, here is a guide: [[COLOR="#0000FF"]http://www.tcpdump.com/kb/os/linux/lvm-renaming.html[/COLOR]]("http://www.tcpdump.com/kb/os/linux/lvm-renaming.html")

This is for the Logical Volume.  You can also rename the Volume Group is something else. That command is: *vgrename*.    Remember that some of this requires that you unmount the volume.  This si something you can't do from your running install.  You would have to boot into a LiveCd Ubuntu then install the NFS tools to deal with you installed volume.  Not pretty, but doable.  Be aware that any mistake could result in you having to re-install.  BACKUP ALL OF YOUR YOUR DATA BEFORE YOU DO THIS.

---

### Post by innocentmani on 2013-07-18
i also faced the same problem..
I am trying to fix the problem,,

---

### Post by steeldriver on 2013-07-18
I tried it for fun yesterday (well not quite - I had a system where I'd reused the root and swap LVs when reinstalling, so that the /dev/mapper/xxx names in /etc/fstab reflected the old hostname)

I found that executing vgrename on an active volume group (with mounted root ans swap logical volumes) and editing fstab didn't appear to immediately break anything, however I forgot to run update-grub and when I tried to reboot I was dropped to grub rescue - I had to chroot in after and fix that (not pretty - boot-repair didn't work for some reason so I had to do it by hand). If you have a separate /boot parition outside of the renamed volume group that might not be necessary.

FWIW I ended up using UUIDs (as reported by blkid) in the new /etc/fstab instead of the /dev/mapper names

If I was doing it again I would probably boot from a live CD / DVD like capscrew recommended, the only wrinkle you will likely face is that most 'desktop' live distributions do not include lvm so you would need to 

```

sudo apt-get install lvm2

```

before you can run vgrename (in fact you likely won't even be able to display the VGs / LVs until you do that). Hope this helps.

---

### Post by capscrew on 2013-07-18
> **steeldriver said:**
> FWIW I ended up using UUIDs (as reported by blkid) in the new /etc/fstab instead of the /dev/mapper names

This creates negative consequences if you use LVM and later create snapshots..  In fact using UUID's has a well known bug.  At the present time you should NOT use UUID's in fstab with LVM2 volumes.  That's why the Ubuntu installer uses /dev/mapper when the install uses LVM.

See here:[COLOR="#0000FF"][ http://forums.opensuse.org/english/get-technical-help-here/install-boot-login/484835-lvm-snapshot-uuid-issue-after-fresh-12-3-install-old-home.html]("http://forums.opensuse.org/english/get-technical-help-here/install-boot-login/484835-lvm-snapshot-uuid-issue-after-fresh-12-3-install-old-home.html")[/COLOR]

---

### Post by steeldriver on 2013-07-18
Ok thanks - I wasn't aware of that,  will fix asap

BTW do you know how it was still mounting with the old mapper names in place?

---

### Post by capscrew on 2013-07-18
> **steeldriver said:**
> 
BTW do you know how it was still mounting with the old mapper names in place?

I can only guess at what you mean here.  Once a filesystem is mounted it stays that way until it is unmounted.  You can change the fstab file and it won't affect anything until you reboot or use the mount command.  Does that help?

---

