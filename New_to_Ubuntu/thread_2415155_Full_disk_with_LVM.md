---
title: "Full disk with LVM"
date: 2019-03-21
forum: New to Ubuntu
---

### Post by ivafa on 2019-03-21
Hi
I have a running local server for over 6 month for office usage. Yesterday I received some update for php 7.2 and every thing was look ok after restarting the server. Update process was asking me about keeping the current php.ini or replacing it with new default one. I check the different's and because all different's was about memory and file size limitations,  I decide to update it.(Backup is available)
This morning nobody was able to login into web base app. I checked the server and finally find out that the reason is there are no more free space on hard disk for application activity.
```
$ ls -lha /var-bash: cannot create temp file for here-document: No space left on device-bash: cannot create temp file for here-document: No space left on device
^C



```

The hard disk has 1TB capacity and I think it's not full.
The partitioning is LMV(The Ubuntu installation suggestion) and I can't understand while it has 931.5G on sda, why it's full?


before some clean up:
```

$ df
Filesystem                        1K-blocks    Used Available Use% Mounted on
udev                                3988856       0   3988856   0% /dev
tmpfs                                803908    1216    802692   1% /run
/dev/mapper/ubuntu--vg-ubuntu--lv   4062912 3994212         0 100% /
tmpfs                               4019536       0   4019536   0% /dev/shm
tmpfs                                  5120       0      5120   0% /run/lock
tmpfs                               4019536       0   4019536   0% /sys/fs/cgroup
/dev/loop0                            93184   93184         0 100% /snap/core/6350
/dev/loop1                            93184   93184         0 100% /snap/core/6405
/dev/loop2                            93312   93312         0 100% /snap/core/6531
/dev/sda2                            999320  224700    705808  25% /boot
/dev/sda1                            523248    6152    517096   2% /boot/efi
tmpfs                                803904       0    803904   0% /run/user/1000



```
after cleanups:
```
$ df -h
Filesystem                         Size  Used Avail Use% Mounted on
udev                               3.9G     0  3.9G   0% /dev
tmpfs                              786M  1.3M  784M   1% /run
/dev/mapper/ubuntu--vg-ubuntu--lv  3.9G  3.0G  757M  80% /
tmpfs                              3.9G     0  3.9G   0% /dev/shm
tmpfs                              5.0M     0  5.0M   0% /run/lock
tmpfs                              3.9G     0  3.9G   0% /sys/fs/cgroup
/dev/loop0                          91M   91M     0 100% /snap/core/6350
/dev/loop1                          91M   91M     0 100% /snap/core/6405
/dev/loop2                          92M   92M     0 100% /snap/core/6531
/dev/sda2                          976M  142M  767M  16% /boot
/dev/sda1                          511M  6.1M  505M   2% /boot/efi
tmpfs                              786M     0  786M   0% /run/user/1000



```
```
$
 lsblk
NAME                      MAJ:MIN RM   SIZE RO TYPE MOUNTPOINT
loop0                       7:0    0    91M  1 loop /snap/core/6350
loop1                       7:1    0    91M  1 loop /snap/core/6405
loop2                       7:2    0  91.1M  1 loop /snap/core/6531
sda                         8:0    0 931.5G  0 disk 
&#9500;&#9472;sda1                      8:1    0   512M  0 part /boot/efi
&#9500;&#9472;sda2                      8:2    0     1G  0 part /boot
&#9492;&#9472;sda3                      8:3    0   930G  0 part 
  &#9492;&#9472;ubuntu--vg-ubuntu--lv 253:0    0     4G  0 lvm  /
sr0                        11:0    1  1024M  0 rom  



```

The question is how can I get more space to work for Ubuntu. Why only 4G is allocated? 

Thanks[FONT=Verdana]
[/FONT]

---

### Post by Dennis N on 2019-03-21
How to extend a LV (logical volume) used by Ubuntu:

Check the volume group with vgdisplay command and see how much space is free:
```

sudo vgdisplay | grep -i free
```
Use lvdisplay command to get the correct LV path:
```
sudo lvdisplay | grep -i path
```
Extend the logical volume to use some of the free space:

To add 20G to the logical volume, copy the LV path from the lvdisplay output and insert in the command where indicated (without the < and > signs):
```
sudo lvextend --resizefs --size +20G <put LV path here>
```

You should now have more space.

---

### Post by ivafa on 2019-03-21
Yes I have enough space now.
Thanks.

---

