---
title: "Unable to hibernate in Ubuntu 16.04 LTS"
date: 2016-07-26
forum: New to Ubuntu
---

### Post by drew123301 on 2016-07-26
I have recently installed Ubuntu 16.04 LTS to run alongside my Windows 10 on my HP Pavilion 17 Notebook PC. My computer is a few years old, and therefore the battery is not what is once was. Generally, I would use hibernate as opposed to sleep in order to save power and extend my battery life, but I have learned that Ubuntu has removed that option a few releases ago. I found several posts saying to edit **/etc/polkit-1/localauthority/50-local.d/com.ubuntu.enable-hibernate.pkla **.  I navigated there and discovered that the file did not exist on my system, so I created it and it currently only has

[Re-enable hibernate by default in upower]
Identity=unix-user:*
Action=org.freedesktop.upower.hibernate
ResultActive=yes


[Re-enable Hibernate by default in logind]
Identity=unix-user:*
Action=org.freedesktop.login1.hibernate;org.freedesktop.login1.handle-hibernate-key;org.freedesktop.login1;org.freedesktop.login1.hibernate-multiple-sessions;org.freedesktop.login1.hibernate-ignore-inhibit
ResultActive=yes

The aforementioned post also said that the hibernate option would appear in my menu once I logged out and logged back in. Since then, I have not only done that, but also restarted the Ubuntu system several times and the option still has not appeared. Lastly, I discovered the terminal command line **sudo pm-hibernate** but when I enter it and enter the my admin password the only thing that happens is that a new command line is created.

---

### Post by nikefalcon on 2016-07-29
I am on **16.04** and **pm-hibernate** works alright for me(on kernels **4.4.0-28-generic** and **4.4.0-31-generic**). Have you tried using systemctl?
```
systemctl hibernate 
```
Although I suspect it won't work because there is some underlying problem.

EDIT:
Which kernel version did you try this on?
Known issues [here]("https://askubuntu.com/questions/761394/why-isnt-hibernate-in-ubuntu-16-04-working-and-how-to-fix-it") and [here]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1566302").

---

### Post by drew123301 on 2016-08-02
I attempted the systemctl hibernate as you suggested and got this result
```

~$ systemctl hibernate
Failed to hibernate system via logind: Sleep verb not supported
```

---

### Post by nikefalcon on 2016-08-02
Hmm..that's not much to go on...please provide more details.

Kernel version:
```
uname -a

```
Filesystems:
```
cat /etc/fstab

```
Memory and swap size:
```

free
swapon --summary

```

---

### Post by QDR06VV9 on 2016-08-02
This is a known bug: [https://github.com/systemd/systemd/issues/2714](https://github.com/systemd/systemd/issues/2714)
The author of systemd is involved in the discussion.
And Here: [https://github.com/systemd/systemd/issues/2528](https://github.com/systemd/systemd/issues/2528)

---

### Post by drew123301 on 2016-08-05
> **nikefalcon said:**
> Hmm..that's not much to go on...please provide more details.

Kernel version:
```
uname -a

```
Filesystems:
```
cat /etc/fstab

```
Memory and swap size:
```

free
swapon --summary

```


I have recently installed TuxOnIce and it has enabled the hibernate power state on my computer. But now coding is as follows:
```
uname -a

Linux DrewsPC 4.4.0-31-generic-tuxonice #50~ppa1-Ubuntu SMP Fri Jul 15 21:15:29 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux

cat /etc/fstab

# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda9 during installation
UUID=441a2998-50df-456c-99e3-db803500e501 /               ext4    errors=remount-ro 0       1
# /boot/efi was on /dev/sda2 during installation
UUID=9A27-F1DC  /boot/efi       vfat    umask=0077      0       1
# swap was on /dev/sda10 during installation
UUID=2cbd951e-b534-487f-938c-e69380e4e5d7 none            swap    sw              0       0

free

              total        used        free      shared  buff/cache   available
Mem:        6000204     1424024     3536260      364676     1039920     3910084
Swap:       6180860           0     6180860


swapon --summary

Filename                Type        Size    Used    Priority
/dev/sda10                                 partition    6180860    0    -1

```

---

### Post by nikefalcon on 2016-08-06
> **runrickus said:**
> This is a known bug: [https://github.com/systemd/systemd/issues/2714](https://github.com/systemd/systemd/issues/2714)
The author of systemd is involved in the discussion.
And Here: [https://github.com/systemd/systemd/issues/2528](https://github.com/systemd/systemd/issues/2528)

Could it be that the bug is hardware dependent then? Because everything works just fine here.

---

