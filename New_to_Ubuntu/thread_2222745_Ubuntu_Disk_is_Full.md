---
title: "Ubuntu Disk is Full"
date: 2014-05-08
forum: New to Ubuntu
---

### Post by Abdelrhman_Shawky on 2014-05-08
Hi,
I'm trying to resize my disk to create more partitions but it says that the whole disk is used , how is that ?

that's the [screenshot]("http://s12.postimg.org/mk0slbcf0/Screenshot_from_2014_05_08_05_56_20.jpg") from gparted.

---

### Post by papibe on 2014-05-08
Hi Abdelrhman_Shawky. Welcome to the forums ):P

Could you open a terminal, run these commands, and post back the results (you can copy/paste the text)?
```
df -h

df -i
```
Regards.

---

### Post by Abdelrhman_Shawky on 2014-05-08
```
booody@BoOodY-PC:~$ df -h
Filesystem                   Size  Used Avail Use% Mounted on
/dev/mapper/ubuntu--vg-root  451G  170G  258G  40% /
none                         4.0K     0  4.0K   0% /sys/fs/cgroup
udev                         3.9G  8.0K  3.9G   1% /dev
tmpfs                        790M  1.1M  789M   1% /run
none                         5.0M     0  5.0M   0% /run/lock
none                         3.9G   54M  3.9G   2% /run/shm
none                         100M   52K  100M   1% /run/user
/dev/sda1                    236M   36M  188M  17% /boot
booody@BoOodY-PC:~$ df -i
Filesystem                    Inodes  IUsed    IFree IUse% Mounted on
/dev/mapper/ubuntu--vg-root 29990912 244336 29746576    1% /
none                         1010181      2  1010179    1% /sys/fs/cgroup
udev                         1007399    503  1006896    1% /dev
tmpfs                        1010181    518  1009663    1% /run
none                         1010181      4  1010177    1% /run/lock
none                         1010181     27  1010154    1% /run/shm
none                         1010181     30  1010151    1% /run/user
/dev/sda1                      62248    301    61947    1% /boot
booody@BoOodY-PC:~$
```

---

### Post by papibe on 2014-05-08
Thanks.

I see that you have LVM set up. I not that familiar with that so let's hope someone else pitch in and continue to help you.

Regards.

---

