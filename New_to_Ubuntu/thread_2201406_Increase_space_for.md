---
title: "Increase space for /"
date: 2014-01-24
forum: New to Ubuntu
---

### Post by gopukrishnan on 2014-01-24
Hi all,

I have a linux server installed as virtual machine in a HyperV server. Initially I used a minimum disk for the server installation and had allocated more disk for it when the / became full. What I did is I have created new partition(primary) with the free space allocated form hyperV and added it into the volume group and extended "/" (/dev/mapper/vg_server1-lv_root). Currently I am in a state where all the primary partitions are already created ( last time I created partition as extended and created a logical volume and added to volume group ). So if I need to add more space from hyperV to the linux, how will it come to the server ? will the extend partition increase automatically or anyway I can add that free space to the / partition ? Hope you get my question.

Thanks,

---

### Post by justleen on 2014-01-24
Basicly the order is HyperV resize (extend) -> LVM resize (extend) -> Filesystem resize.

One you created more disk space in the hyperv, you should be able to see that in your volume group - or if its a new disk, make it a physiscal volulme with pvcreate, add it to the vg-group and then extend the logical volume.

The last step is to resize the filesystem to actually use the expanded size. This can be done with resize2fs/resize4fs for ext2/3 en ext4 partitions

---

