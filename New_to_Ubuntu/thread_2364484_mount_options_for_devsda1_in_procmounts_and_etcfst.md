---
title: "mount options for /dev/sda1 in /proc/mounts and /etc/fstab are not the same"
date: 2017-06-23
forum: New to Ubuntu
---

### Post by skippy95 on 2017-06-23
I am new to Ubuntu and trying to learn/understand why I am seeing different mount options for /dev/sda1 which is my /(root) partition.

/proc/mounts shows the following:
/dev/sda1   /   ext4   rw,relatime,errors=remount-ro,data=ordered   0   0

/etc/fstab shows the following:
# / was on /dev/sda1 during installation
UUID=xxx...   /   ext4   errors=remount-ro   0   1

sudo tune2fs -l /dev/sda1 shows the following:
Default mount options:  user_xattr acl
Errors behavior:  Continue

I see conflicts between the pass option where /proc/mounts shows a zero value and /etc/fstab shows a one value. Which one wins out, or should they both have the same value?

Also, /etc/fstab and /proc/mounts show the value of errors-behavior as remount-ro, and tune2fs shows a value of continue. According to man tune2fs, the behavior of the remount-ro value is to remount the filesystem read-only and the behavior of continue is to continue normal execution. So again, does one of these win out over the over, or should they both be the same?

More info:
/dev/sda1 is located on my only internal hdd.
/dev/sda1 mounts just fine, as far as I know.
I have this thing about needing to know why to everything! :P

Thanks much in advance for your help, skippy95

---

### Post by TheFu on 2017-06-23
/proc/mount is what the current options actually used are. /proc/ is a pseudo-file system.
If there are file system errors, it will be remounted as read-only. This is to prevent further damage, but keep the OS working, if possible.

Unmounted file systems don't show up in /proc/.

You'll never be able to know everything. Simply not possible. ;)

---

### Post by Dennis N on 2017-06-23
/etc/fstab is for mounting devices at startup only. 
/etc/mtab (a link into /proc) shows stuff that is currently mounted and is a dynamic list.

/etc/fstab is the only place the pass number (fsck priority) would be used, so it wins. Don't know why mtab fills the pass number with 0 - maybe just a place holder for that field?

---

### Post by papibe on 2017-06-23
> **skippy95 said:**
> 
I see conflicts between the pass option where /proc/mounts shows a zero value and /etc/fstab shows a one value. Which one wins out, or should they both have the same value?
> **Dennis N said:**
> Don't know why mtab fills the pass number with 0 - maybe just a place holder for that field?
As far as I can tell from reading several resources, proc's zeros are not related with fstab's. They are different things.

Regards.

---

### Post by steeldriver on 2017-06-23
I *think* it's the case that the fs_passno number is only checked at boot time, and is not thereafter available to the /proc pseudo filesystem.

At least this seems to be suggested by a number of online sources e.g. the CPAN [Linux::Proc::Mounts]("http://search.cpan.org/~salva/Linux-Proc-Mounts-0.02/lib/Linux/Proc/Mounts.pm") documentation

> 
Note that there are no methods to get the fs_freq and fs_passno  fields as the kernel those [sic] not store then [sic] internally and the  corresponding entries in /proc/mounts are always 0 and so, useless.



---

### Post by skippy95 on 2017-06-25
Thanks everyone for your quick replies.

Ok, so if I have this right?
- mount uses /etc/fstab to actually mount the block device
- mount uses /etc/mtab and therefore /proc/mounts to show what is actually mounted (currently)
- fsck doesn't look at /etc/mtab or /proc/mounts; it only checks /etc/fstab
- in /proc/mount, the <pass> column is pretty much useless

---

