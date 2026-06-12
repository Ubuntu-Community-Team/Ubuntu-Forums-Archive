---
title: "Opted for full disk &amp; LVM encryption, How to mount disk"
date: 2014-05-26
forum: New to Ubuntu
---

### Post by ubn3 on 2014-05-26
Hi all Greetings,
I have two 80 GB Disk drives. One has win & on another I have made a partition and installed Ubuntu 14.04 LTS & enabled full disk encryption & LVM encryption. I successfully login using pass phrase. How to mount the rest of the 80 GB drive? I tried the following
```
sudo blkid
```
```

I got the following output./dev/sdb5: UUID="12962026-cea3-40ea-8f69-38c978b90bcf" TYPE="crypto_LUKS" 
/dev/mapper/sda5_crypt: UUID="7f0h5m-EfdB-b73i-Ob5c-zGbL-VjTl-1zP6WF" TYPE="LVM2_member" 
/dev/mapper/ubuntu--vg-root: UUID="0ee4b6fe-347b-48c9-b0c6-f27a2336de67" TYPE="ext4" 

```
I tried the following using root,
```
/etc/init.d/cryptdisks start 
```
Output:
```

* Starting remaining crypto disks...                                                                                      * cryptswap1 (skipped, device /dev/disk/by-uuid/0e13cbca-9714-407e-bd97-135312251b48 does not exist)...           [fail] 
 * luks-12962026-cea3-40ea-8f69-38c978b90bcf (starting)..
 * luks-12962026-cea3-40ea-8f69-38c978b90bcf: the precheck for '/dev/disk/by-uuid/12962026-cea3-40ea-8f69-38c978b90bcf' failed:  - The device /dev/disk/by-uuid/12962026-cea3-40ea-8f69-38c978b90bcf contains a filesystem type crypto_LUKS.
 * luks-12962026-cea3-40ea-8f69-38c978b90bcf (failed)...                                                           [fail] 
                                                                                                                   [ OK ]



```
I am new to encryption. Is there a way to access or recover my data or to automount the volume drive ?
Thanks & regards

---

