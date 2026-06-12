---
title: "Output of df: Is there a space problem on my machine?"
date: 2019-03-30
forum: New to Ubuntu
---

### Post by zak100 on 2019-03-30
Hi,
Following is the output of my df command:
```
$ df -m
Filesystem     1M-blocks  Used Available Use% Mounted on
udev                7863     0      7863   0% /dev
tmpfs               1577     3      1575   1% /run
/dev/sda2         937368 54971    834713   7% /
tmpfs               7885   266      7619   4% /dev/shm
tmpfs                  5     1         5   1% /run/lock
tmpfs               7885     0      7885   0% /sys/fs/cgroup
/dev/loop1            92    92         0 100% /snap/core/6531
/dev/loop2           141   141         0 100% /snap/gnome-3-26-1604/82
/dev/loop4             4     4         0 100% /snap/gnome-system-monitor/51
/dev/loop3           144   144         0 100% /snap/gnome-3-28-1804/23
/dev/loop6             3     3         0 100% /snap/gnome-calculator/260
/dev/loop8            54    54         0 100% /snap/core18/782
/dev/loop7            90    90         0 100% /snap/core/6673
/dev/loop10           35    35         0 100% /snap/gtk-common-themes/1122
/dev/loop0            15    15         0 100% /snap/gnome-logs/37
/dev/loop9            91    91         0 100% /snap/core/6405
/dev/loop12          906   906         0 100% /snap/android-studio/73
/dev/loop5           141   141         0 100% /snap/gnome-3-26-1604/70
/dev/loop11           36    36         0 100% /snap/gtk-common-themes/1198
/dev/loop16            1     1         0 100% /snap/gnome-logs/57
/dev/loop15            4     4         0 100% /snap/gnome-system-monitor/57
/dev/loop14            5     5         0 100% /snap/gnome-calculator/352
/dev/loop13            3     3         0 100% /snap/gnome-calculator/180
/dev/loop17            4     4         0 100% /snap/gnome-system-monitor/70
/dev/loop18          905   905         0 100% /snap/android-studio/71
/dev/loop19          141   141         0 100% /snap/gnome-3-26-1604/78
/dev/loop20           15    15         0 100% /snap/gnome-logs/45
/dev/loop21           13    13         0 100% /snap/gnome-characters/139
/dev/loop22           13    13         0 100% /snap/gnome-characters/103
/dev/loop24           15    15         0 100% /snap/gnome-characters/206
/dev/loop23           35    35         0 100% /snap/gtk-common-themes/319
/dev/sda1            511     7       505   2% /boot/efi
tmpfs               1577     1      1577   1% /run/user/121
tmpfs               1577     1      1577   1% /run/user/1000
zulfi@lc2530hz:~$ 
```

The above is show that most of the usability is 100% and availability is zero. Please guide me how to fix this problem.

Zulfi.

---

### Post by Bashing-om on 2019-03-30
zak100; Hello -

No, no problem with disk space, The loop device is virtual - only as much needed is allocated and all is used,
 
- hope this helps -

---

### Post by zak100 on 2019-03-30
Hi,
Thanks for your quick reply. God bless you. Actually I installed some virtual machines on my system. But then I can't use USB on virtual machine so I manually deleted the virtual box and all the virtual machines from the "virtualBox VMS" folder.  Is some of hard disk storage still tied to it? Please guide me how to release that memory  without harming my new virtualbox and newly installed virtual machines?
.

Zulfi.

---

### Post by Bashing-om on 2019-03-30
zak100; Well -

That does explain the existence of 24 loop devices. As to how to make sure the VMs are completely removed, sorry I have no experience there. Others will have to advise in this instance.

 A know-it-all I am not

---

### Post by #&amp;thj^% on 2019-03-30
Just a friendly heads-up, never manually delete any installed software on Linux, it will come back and bite you.
First check what is left behind with:
```
VBoxManage list vms
```
and:
```

VBoxManage unregistervm
```
**It would be a good Idea to post back the return of the above commands before proceeding to any of the below.**
To clean up the left-overs
From command line (Or the Terminal) with the following command:
```

VBoxManage unregistervm --delete "<Name of Machine>"
```

By doing so the following files will be deleted:
[list]
        [*]all hard disk image files, including differencing files, which are used by the machine and not shared with other machines;
        [*]saved state files that the machine created, if any (one if the machine was in "saved" state and one for each online snapshot);
        [*]the machine XML file and its backups;
        [*]the machine log files, if any;
        [*]the machine directory, if it is empty after having deleted all the above.[/list]

---

