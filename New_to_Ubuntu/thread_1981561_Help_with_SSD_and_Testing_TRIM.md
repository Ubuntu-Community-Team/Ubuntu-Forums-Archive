---
title: "Help with SSD and Testing TRIM"
date: 2012-05-17
forum: New to Ubuntu
---

### Post by DoctorAcula on 2012-05-17
Hey guys, 

I'm fairly new to linux and just installed Ubuntu 12.04 on an SSD. I have done a little searching and found out how to enable TRIM support for it, and have followed the steps at this site: [http://techgage.com/article/enabling_and_testing_ssd_trim_support_under_linux/](http://techgage.com/article/enabling_and_testing_ssd_trim_support_under_linux/)

I am at the stage of testing to see if TRIM is actually working as it should, but when I enter the command

hdparm --fibmap testfile

I get the error: 

0,19: drive not found in /dev

output in the terminal. Any ideas on why and how to fix it? By the way, I enabled home directory encryption when I installed ubuntu, if that affects anything.

Any help would be appreciated. Thanks.

---

### Post by lkraemer on 2012-05-17
DoctorAcula,
Why don't you post the output of the following Terminal Commands:
```

sudo blkid
cat /etc/fstab

```
Let's assume your SSD is /dev/sdc and the Partition is 6
type the following Terminal Command, except substitute your information:
```

ls -alt /dev/sdc6

```
Post the output of the above commands.


lk

---

### Post by DoctorAcula on 2012-05-17
Hey lkraemer, thanks for the reply!

Here is the output of the command sudo blkid:

/dev/sda1: UUID="dd23fa11-5129-43f7-af17-0f06461180ee" TYPE="ext4" 
/dev/mapper/cryptswap1: UUID="a0228443-408b-4382-aacf-9811833fc122" TYPE="swap" 

And here is the output for cat /etc/fstab

# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=dd23fa11-5129-43f7-af17-0f06461180ee /      ext4 noatime,discard,errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
#UUID=fb32db0e-f99c-4ba9-a3b0-a6c9673cc746 none            swap    sw              0       0
/dev/mapper/cryptswap1 none swap sw 0 0

And here is the output for ls -alt /dev/sda1

brw-rw---- 1 root disk 8, 1 May 17 13:42 /dev/sda1

---

### Post by lkraemer on 2012-05-17
I don't see anything obvious...........Can you post the output of:
```

mount

```

I tried the same commands to generate the seq number 'testfile'
Here is what I got:
> 
larry@debian:~$ sudo hdparm --fibmap testfile
[sudo] password for larry: 

testfile:
 filesystem blocksize 4096, begins at LBA 31033344; assuming 512 byte sectors.
 byte_offset  begin_LBA    end_LBA    sectors
           0  169018624  169018631          8
larry@debian:~$



lk

---

### Post by DoctorAcula on 2012-05-18
Thanks for the reply again.

I think the issue has to do with my home folder being encrypted. I used this command:

sudo dd if=/dev/urandom of=tempfile count=100 bs=512k oflag=direct

in / to create a file and the procedure in the article to test it.
It worked as expected. I could not use seq 1 100 >tempfile to create it, I got a permission denied error,
even using sudo, but I found the above command in another thread ([http://askubuntu.com/questions/18903/how-to-enable-trim](http://askubuntu.com/questions/18903/how-to-enable-trim)) and it worked.

I could not use the above dd command in my Desktop directory. Do you know why?

Another curious thing, I couldn't find AHCI to enable in my BIOS, and searching online shows me [http://www.evga.com/forums/tm.aspx?m=16716&mpage=1](http://www.evga.com/forums/tm.aspx?m=16716&mpage=1),
which says that my mobo doesn't support AHCI, which I was under the impression was necessary for TRIM to work...yet the procedure in the article seems to show otherwise (I get 0000s read out after deleting the file and reading the sector again). 
Any idea why?

Here is the output of mount, by the way:

/dev/sda1 on / type ext4 (rw,noatime,discard,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
udev on /dev type devtmpfs (rw,mode=0755)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755)
none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880)
none on /run/shm type tmpfs (rw,nosuid,nodev)
/home/kevin/.Private on /home/kevin type ecryptfs (ecryptfs_check_dev_ruid,ecryptfs_cipher=aes,ecryptfs_key_bytes=16,ecryptfs_unlink_sigs,ecryptfs_sig=beabe466b772fc01,ecryptfs_fnek_sig=68b74fec1a48ad1b)
gvfs-fuse-daemon on /home/kevin/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=kevin)

If you have any insight into these issues it would be great, but thanks for taking the time to help no matter what. Looks like I have a lot to learn about linux and linux commands and hard drives and TRIM etc etc before I fully understand what's going on.

---

### Post by lkraemer on 2012-05-18
Nope, sorry I haven't a clue.  You are into stuff I haven't used.

Good Luck.

lk

---

