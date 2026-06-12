---
title: "problem with writing into other's linux partition"
date: 2007-06-02
forum: Other OS Talk
---

### Post by szymon_g on 2007-06-02
hi.
i recently installed archlinux onto my computer.
i've installed it becouse i'd like to try something new :P
but now i've got a small problem: i can write into this partitions only by using sudo.
this is my ubuntu's fstab :

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda6
UUID=985f1df6-66ee-452a-bcd1-a65055760dfa /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda7
UUID=25f3a665-1256-4021-afa5-a4017451b4ec /home           xfs     defaults        0       2
# /dev/sda2
UUID=b36dff29-2adc-4020-a512-33dc48b37fa0 /mnt/arch/boot  ext3    rw,auto,users,noatime        0       0
# /dev/sda5
UUID=d3af3504-c56d-4d7e-9f8e-a3f73211545d /mnt/arch/glowna xfs     rw,auto,users,noatime        0       0
# /dev/sda1
UUID=322a45ae-a320-4f10-8256-93f7b0738a0c none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0

i've mounted arch's partitions (sda2 and sda5) into /mnt/arch/boot and /mnt/arch/glowna.
is there any way to write into these partitions as easy (and without need to fix filesystems with every boot) as it would by my 'native' partition?

szymon

---

### Post by kidders on 2007-06-03
Hi there,

It's quite normal to be prevented from making arbitrary changes to Linux filesystems as an unprivileged user ... whether they belong to the distro you've booted up in or not. Consider...[LIST]
[*]**touch /boot/test** vs **touch /mnt/arch/boot/test**
[*]**rm -R /usr** vs **rm -R /mnt/arch/glowna/usr**[/LIST]These should, of course, all fail ... unless they're executed by root. It's also noteworthy that both occurrences of the "users" directive in the /etc/fstab you posted are inappropriate, and should be removed.

Having said all that, you would still expect that something you created using your personal account in one distro should be modifiable with the corresponding account in the other. You may want to check that your accounts' UIDs are the same in both environments, so your filesystems behave as expected.

You also mentioned having to "fix" filesystems ... that's worrying. (Can you be more specific?) Virtually all Linuxes use almost identical implementations of Ext3 and XFS, so they should be flawlessly intercompatible. You really shouldn't need to fix anything!

One other (totally random!) thing that occurs to me is that you might, for safety, like to switch "noauto" for "auto" (or "ro" for "rw") in the mount options for /mnt/arch/boot. When people go to the trouble of creating dedicated /boot partitions, it's normal practice to leave them unmounted (or perhaps mounted read-only), in case accidental damage causes the next boot to fail. Just like typing **sudo**, having to do either of the following reminds people to stop for a second, and think about what they're doing:

**mount -o remount,rw /boot** [SIZE=1](to switch /boot to read/write mode)[/SIZE]
**mount /boot** [SIZE=1](if "noauto" was used in /etc/fstab)[/SIZE]

[COLOR=Silver][[SIZE=1]*[UAResolved]*[/SIZE]]("http://ubuntuforums.org/showthread.php?t=377083")[/COLOR]

---

