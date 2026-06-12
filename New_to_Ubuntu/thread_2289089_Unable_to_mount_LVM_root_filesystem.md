---
title: "Unable to mount LVM /root filesystem"
date: 2015-08-01
forum: New to Ubuntu
---

### Post by Vaibhav_Karve on 2015-08-01
While installing Lubuntu, I chose the install with LVM option. After using it for many days, I wished to reduce the size of my /root from 900GB down to 300GB. I did this using the LVM GUI without using a Live CD! (I realize now that this was a serious mistake). LVM showed me that the /root filesystem did reduce to the desired size of 300G. However, on reboot I realized that the system is broken. Please show me a way to restore my /root partition, without having to completely clean and reinstall the filesystem.

Any help is much appreciated.

---

### Post by vidtek on 2015-08-01
> **Vaibhav_Karve said:**
> While installing Lubuntu, I chose the install with LVM option. After using it for many days, I wished to reduce the size of my /root from 900GB down to 300GB. I did this using the LVM GUI without using a Live CD! (I realize now that this was a serious mistake). LVM showed me that the /root filesystem did reduce to the desired size of 300G. However, on reboot I realized that the system is broken. Please show me a way to restore my /root partition, without having to completely clean and reinstall the filesystem.

Any help is much appreciated.

VK-
You don't give much detail-try this from my earlier post.
[http://ubuntuforums.org/showthread.php?t=2289087](http://ubuntuforums.org/showthread.php?t=2289087)


Cheers, Tony.

---

### Post by Vaibhav_Karve on 2015-08-01
```
lubuntu@lubuntu:~$ blkid
/dev/loop0: TYPE="squashfs" 
/dev/sda1: UUID="9B74-C671" TYPE="vfat" 
/dev/sda2: UUID="cffe7e9c-89a4-47ce-8fff-553c40aaf87c" TYPE="ext2" 
/dev/sda3: UUID="CIufq8-wG3G-ft0M-VTVl-FbBw-3z6Y-aEntT9" TYPE="LVM2_member" 
/dev/mapper/lubuntu--vg-root: UUID="24422202-25c3-4903-a5e4-016de8b72907" TYPE="ext4" 
/dev/mapper/lubuntu--vg-swap_1: UUID="ca5d823c-211d-4ccf-9901-45ae5acb87b2" TYPE="swap" 
/dev/sdb1: LABEL="VAIBHAV PEN" UUID="2297-70B3" TYPE="vfat" 
/dev/zram0: UUID="4f914913-8447-4739-b988-57d9b5b173aa" TYPE="swap" 
/dev/zram1: UUID="fdc55086-34ac-4999-8a18-0288a23c165f" TYPE="swap" 
/dev/zram2: UUID="98682606-a64f-4494-a412-3a3911b3a80e" TYPE="swap" 
/dev/zram3: UUID="a3124d4f-fd7c-4f88-86a2-799d97a02b3c" TYPE="swap"

lubuntu@lubuntu:~$ mount /dev/mapper/lubuntu--vg-root /mnt
mount: only root can do that
lubuntu@lubuntu:~$ sudo mount /dev/mapper/lubuntu--vg-root /mnt
mount: wrong fs type, bad option, bad superblock on /dev/mapper/lubuntu--vg-root,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

```

Tony, here's the output.

---

### Post by vidtek on 2015-08-01
> **Vaibhav_Karve said:**
> ```
lubuntu@lubuntu:~$ blkid
/dev/loop0: TYPE="squashfs" 
/dev/sda1: UUID="9B74-C671" TYPE="vfat" 
/dev/sda2: UUID="cffe7e9c-89a4-47ce-8fff-553c40aaf87c" TYPE="ext2" 
/dev/sda3: UUID="CIufq8-wG3G-ft0M-VTVl-FbBw-3z6Y-aEntT9" TYPE="LVM2_member" 
/dev/mapper/lubuntu--vg-root: UUID="24422202-25c3-4903-a5e4-016de8b72907" TYPE="ext4" 
/dev/mapper/lubuntu--vg-swap_1: UUID="ca5d823c-211d-4ccf-9901-45ae5acb87b2" TYPE="swap" 
/dev/sdb1: LABEL="VAIBHAV PEN" UUID="2297-70B3" TYPE="vfat" 
/dev/zram0: UUID="4f914913-8447-4739-b988-57d9b5b173aa" TYPE="swap" 
/dev/zram1: UUID="fdc55086-34ac-4999-8a18-0288a23c165f" TYPE="swap" 
/dev/zram2: UUID="98682606-a64f-4494-a412-3a3911b3a80e" TYPE="swap" 
/dev/zram3: UUID="a3124d4f-fd7c-4f88-86a2-799d97a02b3c" TYPE="swap"

lubuntu@lubuntu:~$ mount /dev/mapper/lubuntu--vg-root /mnt
mount: only root can do that
lubuntu@lubuntu:~$ sudo mount /dev/mapper/lubuntu--vg-root /mnt
mount: wrong fs type, bad option, bad superblock on /dev/mapper/lubuntu--vg-root,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

```

Tony, here's the output.

I don't understand your /dev path, it doesn't make any sense.

your command should be more like :

sudo mount /dev/sd?? /mnt

what is this /dev/mapper/lubuntu--vg-root ??

Tony

---

### Post by Vaibhav_Karve on 2015-08-01
> **vidtek said:**
> 

what is this /dev/mapper/lubuntu--vg-root ??

Tony

That is the default name that LVM chose for my /root. I did not change that name. The root and swap are a part of /dev/sda3.

---

### Post by vidtek on 2015-08-01
> **Vaibhav_Karve said:**
> That is the default name that LVM chose for my /root. I did not change that name. The root and swap are a part of /dev/sda3.

VK-

Can't say I'm sure about LVM's but to sort your problem you would probably need to go to the actual hdd which as you say is sda3.

you could try mounting that (and probably really stuff it up).

LVM's are a real pain-I learned early on they're more trouble than they're worth, especially now storage is so cheap.

Tony.

---

### Post by Vaibhav_Karve on 2015-08-01
> **vidtek said:**
> VK-

Can't say I'm sure about LVM's but to sort your problem you would probably need to go to the actual hdd which as you say is sda3.

you could try mounting that (and probably really stuff it up).


Here's the output for that --
```

lubuntu@lubuntu:~$ sudo mount /dev/sda3 /mnt
mount: unknown filesystem type 'LVM2_member'

```

> 
LVM's are a real pain-I learned early on they're more trouble than they're worth, especially now storage is so cheap.

Tony.

Thanks Tony. But be that as it may, right now I have little option but to try and restore my system on LVMs.

---

### Post by vidtek on 2015-08-01
> **Vaibhav_Karve said:**
> Here's the output for that --
```

lubuntu@lubuntu:~$ sudo mount /dev/sda3 /mnt
mount: unknown filesystem type 'LVM2_member'

```



Thanks Tony. But be that as it may, right now I have little option but to try and restore my system on LVMs.

VK-

Another tutorial on chroot that is supposed to work for LVM's

[https://help.ubuntu.com/community/Grub2/Installing#via_ChRoot](https://help.ubuntu.com/community/Grub2/Installing#via_ChRoot)

Cheers Tony.

---

### Post by sandyd on 2015-08-02
Can you post the output of
```

lvdisplay
vgdisplay
ls -l /dev/mapper/
```

Commands may require sudo.

If you did not do the correct procedure to resize the root partition, or miscalculated, the LVM will have chopped off part of your root partition
Partitions in a LV have to be resized before resizing LV (Logical Volume), otherwise partition will be cut off
If calculations are incorrect and you shrink more than you should have, you will chop off part of the root partition as well.
Its entirely possible that your data is still there if you haven't done anything else other than resizing that one LV. In this case, we can just try to re-extend the LV to see if the data reappears. Since it is standard in Ubuntu LVM setups to have no free space, we can just extend LV to maximum size.

Should be just
```

sudo lvextend -l +100%FREE /dev/mapper/lubuntu--vg-root
sudo e2fsck -f /dev/mapper/lubuntu--vg-root

```
but we should probably check the output of the commands above to see if there are any issues before we begin extending.

Then, to resize again after FS is confirmed working:
```

sudo lvreduce -r -L 300G /dev/mapper/lubuntu--vg-root
```

---

