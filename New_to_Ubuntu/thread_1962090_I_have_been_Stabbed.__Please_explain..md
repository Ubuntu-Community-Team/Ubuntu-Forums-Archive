---
title: "I have been Stabbed.  Please explain."
date: 2012-04-20
forum: New to Ubuntu
---

### Post by Boyntonstu on 2012-04-20
boyntonstu@boyntonstu-s5704y:~$ sudo cat /etc/fstab
[sudo] password for boyntonstu: 
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb5 during installation
UUID=9c950be4-4d95-4e18-b41a-6c6e1fc5fb72 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb6 during installation
UUID=b8e517ac-d381-4df1-ac46-e05e49d1afbc none            swap    sw              0       0
boyntonstu@boyntonstu-s5704y:~$

---

### Post by jerome1232 on 2012-04-20
What is wrong with your fstab again? It looks like a typical, single partition install.

---

### Post by Cheesemill on 2012-04-20
There's nothing wrong with that.

What's your problem or what needs explaining?

---

### Post by Boyntonstu on 2012-04-20
> **Cheesemill said:**
> There's nothing wrong with that.

What's your problem or what needs explaining?

    errors=remount-ro 0       1

---

### Post by jerome1232 on 2012-04-20
That means if there are errors in file system, it will be remounted as read only. The numbers at the end tell the system to not backup the filesystem, and to check it on the first pass.

---

### Post by oldos2er on 2012-04-20
> **Boyntonstu said:**
> boyntonstu@boyntonstu-s5704y:~$ sudo cat /etc/fstab

Don't use 'sudo' unless it's absolutely necessary, and it's not for the above.

[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)

Edit: It helps if you have a question to just ask it directly, rather than making people who're trying to help you guess what it is. Just FYI.

---

