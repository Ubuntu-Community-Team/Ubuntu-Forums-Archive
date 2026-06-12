---
title: "[SOLVED] special device /dev/mapper/encr-hdd_1 does not exist?"
date: 2008-11-04
forum: New to Ubuntu
---

### Post by hopelessone on 2008-11-04
Hi,

I followed:

[http://www.g-loaded.eu/2005/11/10/encrypt-devices-using-dm-crypt-and-luks/](http://www.g-loaded.eu/2005/11/10/encrypt-devices-using-dm-crypt-and-luks/)

then :

[http://www.howtoforge.com/automatically-unlock-luks-encrypted-drives-with-a-keyfile](http://www.howtoforge.com/automatically-unlock-luks-encrypted-drives-with-a-keyfile)

and i get this:
some@box:~$ sudo mount -a
mount: special device /dev/mapper/encr-hdd_1 does not exist
some@box:~$ 


I am lost...what can i do to fix this?

fstab:
/dev/mapper/encr-hdd_1 /mnt/hdd_1      ext3    defaults        0       2

crypttab:
encr-hdd_1 /dev/disk/by-uuid/ac212449-9edc-4871-b78d-b059523d2fff /root/keyfile  luks

Thanks...

---

### Post by hopelessone on 2008-11-04
please help ...

i think i lost everything...

i can't find any info...to help...please please please....help..me..

---

### Post by hopelessone on 2008-11-04
i did:
unmount
format ext3
sudo tune2fs -m 0 /dev/sda1
sudo badblocks -c 10240 -s -w -t random -v /dev/sda1
sudo cryptsetup --verbose --cipher "aes-cbc-essiv:sha256" --key-size 256 --verify-passphrase luksFormat /dev/sda1
sudo cryptsetup luksOpen /dev/sda1 encr-hdd_1
sudo mkfs.ext3 -j -m 1 -O dir_index,filetype,sparse_super /dev/mapper/encr-hdd_1
sudo chown -R some:some /dev/mapper/encr-hdd_1

---

### Post by hopelessone on 2008-11-04
i think i didn't unmount it properly ... i just rebooted...

---

### Post by hopelessone on 2008-11-04
some@box:~$ sudo e2fsck -p /dev/mapper/encr-hdd_1
e2fsck: No such file or directory while trying to open /dev/mapper/encr-hdd_1
/dev/mapper/encr-hdd_1: 
The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>

some@box:~$

---

### Post by hopelessone on 2008-11-04
some@box:~$ sudo mke2fs -n /dev/sda1
mke2fs 1.41.3 (12-Oct-2008)
Filesystem label=
OS type: Linux
Block size=4096 (log=2)
Fragment size=4096 (log=2)
18317312 inodes, 73258400 blocks
3662920 blocks (5.00%) reserved for the super user
First data block=0
Maximum filesystem blocks=4294967296
2236 block groups
32768 blocks per group, 32768 fragments per group
8192 inodes per group
Superblock backups stored on blocks: 
	32768, 98304, 163840, 229376, 294912, 819200, 884736, 1605632, 2654208, 
	4096000, 7962624, 11239424, 20480000, 23887872, 71663616

---

### Post by hopelessone on 2008-11-04
some@box:~$ blkid
/dev/sda1: UUID="ac212449-9edc-4871-b78d-b059523d2fff" TYPE="ext3" SEC_TYPE="ext2"

---

### Post by hopelessone on 2008-11-04
*bump*

---

### Post by bodhi.zazen on 2008-11-04
I can see you are having problems, but I can not tell exactly what.

See this thread for how to mount an encrypted partition :

[http://ubuntuforums.org/showthread.php?p=4530641](http://ubuntuforums.org/showthread.php?p=4530641)

You need to unlock the crypt :

sudo cryptsetup luksOpen <partition> <name_of_crypt> <key>

---

### Post by pinguim007 on 2012-09-24
relax man,

don't insert commands without understand the theory, I am having the same problem with a non encrypted system...

I think the theory that you are looking for is device mapper.

I will try to solve the problem and I will later post here in case you don't solve before.

See you...

---

### Post by sandyd on 2012-09-24
**Necromancy - Thread closed**

As per the [Ubuntu Forums code of conduct]("http://ubuntuforums.org/index.php?page=policy"), please do not post in threads more than one year old, as a lot of things can change over time.

Thanks!

---

