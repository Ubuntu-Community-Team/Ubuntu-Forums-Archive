---
title: "Cannot find solution for Target filesystem doesn't have /sbin/init"
date: 2012-03-14
forum: New to Ubuntu
---

### Post by archie569 on 2012-03-14
I cannot boot into ubuntu, init file not found, but windows works perfectly. 

Cause of problem: Resize ubuntu partition.

My partitions are:
/dev/sda1 ntfs (unlocked) 100 MiB             (Windows: Working)      Flag: none
/dev/sda2 ntfs (unlocked) 336.09 GiB        (windows: working)      Flag: none
unallocated unallocated (unlocked) 1.49 MiB                                  Flag:none
/dev/sda3 extended (locked) 259.98 GiB                                       Flag:boot
{
     /dev/sda5 ext4 (unlocked) 252.35 GiB
    /dev/sda6 linux-swap (locked) 7.63 GiB             
}
 
Please considered that all of this options that I tried were performed in terminal after booting in the Live CD of ubuntu 11.04: 

1)   sudo e2fsck -f -y -v /dev/sda5 
           Results: 
            All passes without any problem, just in pass 5: "File system was modified"
2)  tried to boot in grub (recovery mode). Ends with same warning: init file not found. 
3) in Gparted right click in sda5 and Check, no problems. 
4) when I type sudo frisk -l, it basically just lists all the partitions, noting new.
5) I tried also:
        sudo mount /dev/sda5 /mnt
        sudo grub-install --root-directory=/mnt /dev/sda

None of these worked, still I have the missing init file for my partition. Please help me. 
Thank you

---

