---
title: "Encrypted swap problems in UbuntuGnome 16.4.3 LTS"
date: 2018-02-12
forum: New to Ubuntu
---

### Post by linurandy on 2018-02-12
Hello to everyone, I'm relative new in Ubuntu. I came from Debian. My problem is I installed Ubuntu with two encrypted partitions, *swap* and *external disk*, 'cause i have a SSD(128GB) disk and HDD(1TB) disk. When i reboot the swap doesn't up.
There is a error:
```
systemctl status [EMAIL="systemd-cryptsetup@sdb3_crypt.servic"]systemd-cryptsetup@sdb3_crypt.servic[/EMAIL]e
[EMAIL="systemd-cryptsetup@sdb3_crypt.servic"]systemd-cryptsetup@sdb3_crypt.servic[/EMAIL]e - Cryptography Setup for sdb3_crypt
   Loaded: loaded (/etc/crypttab; bad; vendor preset: enabled)
   Active: inactive (dead)
     Docs: man:crypttab(5)
           man:systemd-cryptsetup-generator(8)
           man:systemd-cryptsetup@.service(8)

feb 12 16:05:56 eloy systemd[1]: Dependency failed for Cryptography Setup for sdb3_crypt.
feb 12 16:05:56 eloy systemd[1]: [EMAIL="systemd-cryptsetup@sdb3_crypt.servic"]systemd-cryptsetup@sdb3_crypt.servic[/EMAIL]e: Job [EMAIL="systemd-cryptsetup@sdb3_crypt.servic"]systemd-cryptsetup@sdb3_crypt.servic[/EMAIL]e/start failed with result 'dependency'.
feb 12 16:07:27 eloy systemd[1]: Dependency failed for Cryptography Setup for sdb3_crypt.
feb 12 16:07:27 eloy systemd[1]: [EMAIL="systemd-cryptsetup@sdb3_crypt.servic"]systemd-cryptsetup@sdb3_crypt.servic[/EMAIL]e: Job [EMAIL="systemd-cryptsetup@sdb3_crypt.servic"]systemd-cryptsetup@sdb3_crypt.servic[/EMAIL]e/start failed with result 'dependency'
```.

[B]/etc/crypttab
[/B]```
sdb3_crypt UUID=ec068b69-c35b-406f-b6dc-1292799e9b90 none luks,swap,discard
sda1_crypt UUID=5b1e9d0f-b740-46c3-8331-d910e6df94a8 none luks,discard
```

[B]/etc/fstab
[/B]```
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sdb4 during installation
UUID=b584ce30-188c-417b-9aa7-862030fa7fa8 /               ext4    errors=remount-ro 0       1
# /boot was on /dev/sdb2 during installation
UUID=4f9ab339-bf68-475c-b666-cd288ea1a800 /boot           ext2    defaults        0       2
# /boot/efi was on /dev/sdb1 during installation
UUID=C830-A98A  /boot/efi       vfat    umask=0077      0       1
# /home was on /dev/sdb5 during installation
UUID=2d69c129-4e53-4a9d-bd96-328a1b1277f1 /home           ext4    defaults        0       2
/dev/mapper/sda1_crypt /media/Datos    ext4    defaults        0       2
/dev/mapper/sdb3_crypt none            swap    sw              0       0
```

**sudo lsblk **
```
NAME           MAJ:MIN RM   SIZE RO TYPE  MOUNTPOINT
sdb              8:16   0 119,2G  0 disk  
&#9500;&#9472;sdb4           8:20   0  28,6G  0 part  /
&#9500;&#9472;sdb2           8:18   0 333,8M  0 part  /boot
&#9500;&#9472;sdb5           8:21   0  82,5G  0 part  /home
&#9500;&#9472;sdb3           8:19   0   7,6G  0 part  
&#9492;&#9472;sdb1           8:17   0   234M  0 part  /boot/efi
sda              8:0    0 931,5G  0 disk  
&#9492;&#9472;sda1           8:1    0 931,5G  0 part  
  &#9492;&#9472;sda1_crypt 253:0    0 931,5G  0 crypt /media/Datos
```

**sudo blkid **
```
/dev/sda1: UUID="5b1e9d0f-b740-46c3-8331-d910e6df94a8" TYPE="crypto_LUKS" PARTUUID="d5124512-c9ac-47a5-9e66-27a0dd65aea4"
/dev/sdb1: UUID="C830-A98A" TYPE="vfat" PARTUUID="908adf79-802c-4265-a8f3-0d8675d44877"
/dev/sdb2: UUID="4f9ab339-bf68-475c-b666-cd288ea1a800" TYPE="ext2" PARTUUID="a41e6b55-b5b2-430f-b2cb-f18e6da04bee"
/dev/sdb4: UUID="b584ce30-188c-417b-9aa7-862030fa7fa8" TYPE="ext4" PARTUUID="3fb84098-5d38-4bea-9741-fa96e0cbd800"
/dev/sdb5: UUID="2d69c129-4e53-4a9d-bd96-328a1b1277f1" TYPE="ext4" PARTUUID="b78ed599-e0a6-4ec8-bc65-068b7b8f65ca"
/dev/mapper/sda1_crypt: LABEL="Datos" UUID="3e0cc9fa-6e9b-4e00-a850-2301d7ce24e0" TYPE="ext4"
/dev/sdb3: PARTUUID="d8044448-ead7-4406-b65e-48e2acd3cc4f"
```

I don't know what is the error.

---

### Post by TheFu on 2018-02-12
Please edit all the command output using "code tags" - they are under the "Advanced" editor.  Too hard to read otherwise.

Are the passphrases for both storage the same?

---

