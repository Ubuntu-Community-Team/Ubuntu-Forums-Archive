---
title: "4TB Seagate stdr4000100 external drive not showing up in Ubuntu"
date: 2019-01-04
forum: New to Ubuntu
---

### Post by timbrown527 on 2019-01-04
Hello!

New to Ubuntu (moving from PCLinuxOS), trying to upgrade from a 1TB Seagate (which works fine) to a 4 TB Seagate external drive. Plugged the drive in, it lit up and was spinning but did not show up in the file manager.

Did a search, but found nothing on this. Anyone have a handle on what's going on?

thanks,

Tim

---

### Post by Dennis N on 2019-01-04
Has a partition table been created on the new drive? Did you create at least one partition with an ext4 file system? The file manager won't show the drive without one.

---

### Post by timbrown527 on 2019-01-04
Should be plug and play. the 1Tb drive was that way. In any case, it doesn't even show up as a drive. At. All. So, doing anything with it (as it is) is out of the question.

---

### Post by QIII on 2019-01-04
Hello!

Would you please issue the following in the terminal and post the results?

```
sudo blkid
```

followed by the results of

```
df -h
```

That will tell us whether the OS is identifying the drive.

Again: The file manager will not show anything if there is no partition table.

---

### Post by timbrown527 on 2019-01-04
> **QIII said:**
> Hello!

Would you please issue the following in the terminal and post the results?

```
sudo blkid
```

followed by the results of

```
df -h
```

That will tell us whether the OS is identifying the drive.

Again: The file manager will not show anything if there is no partition table.

Here:

```

tim@tim-HP-Compaq-6005-Pro-MT-PC:~$ sudo blkid
[sudo] password for tim: 
/dev/loop0: TYPE="squashfs"
/dev/loop1: TYPE="squashfs"
/dev/loop2: TYPE="squashfs"
/dev/loop3: TYPE="squashfs"
/dev/loop4: TYPE="squashfs"
/dev/loop5: TYPE="squashfs"
/dev/loop6: TYPE="squashfs"
/dev/loop7: TYPE="squashfs"
/dev/sda1: UUID="b08b4633-18ab-4cb4-8d68-051ab81bf9aa" TYPE="ext4" PARTUUID="c3f33bd8-01"
/dev/loop8: TYPE="squashfs"
/dev/loop9: TYPE="squashfs"
/dev/loop10: TYPE="squashfs"
/dev/loop11: TYPE="squashfs"
/dev/loop12: TYPE="squashfs"
/dev/loop13: TYPE="squashfs"
/dev/loop14: TYPE="squashfs"
tim@tim-HP-Compaq-6005-Pro-MT-PC:~$ 
```

...and...

```

tim@tim-HP-Compaq-6005-Pro-MT-PC:~$ df -h
Filesystem      Size  Used Avail Use% Mounted on
udev            4.6G     0  4.6G   0% /dev
tmpfs           949M  1.6M  948M   1% /run
/dev/sda1       458G   21G  414G   5% /
tmpfs           4.7G   20M  4.7G   1% /dev/shm
tmpfs           5.0M  4.0K  5.0M   1% /run/lock
tmpfs           4.7G     0  4.7G   0% /sys/fs/cgroup
/dev/loop0       87M   87M     0 100% /snap/core/4917
/dev/loop2      2.3M  2.3M     0 100% /snap/gnome-calculator/260
/dev/loop1       15M   15M     0 100% /snap/gnome-logs/45
/dev/loop3       13M   13M     0 100% /snap/gnome-characters/103
/dev/loop6       15M   15M     0 100% /snap/gnome-logs/37
/dev/loop8       35M   35M     0 100% /snap/gtk-common-themes/319
/dev/loop4      2.4M  2.4M     0 100% /snap/gnome-calculator/180
/dev/loop7      3.8M  3.8M     0 100% /snap/gnome-system-monitor/51
/dev/loop5      195M  195M     0 100% /snap/mailspring/309
/dev/loop9      141M  141M     0 100% /snap/gnome-3-26-1604/70
/dev/loop10      90M   90M     0 100% /snap/core/6130
/dev/loop12     3.8M  3.8M     0 100% /snap/gnome-system-monitor/57
/dev/loop14      35M   35M     0 100% /snap/gtk-common-themes/818
/dev/loop11     141M  141M     0 100% /snap/gnome-3-26-1604/74
/dev/loop13      13M   13M     0 100% /snap/gnome-characters/139
tmpfs           949M   40K  949M   1% /run/user/1000
tim@tim-HP-Compaq-6005-Pro-MT-PC:~$
```

---

### Post by QIII on 2019-01-04
OK.  Next question:  Does it appear in your BIOS/UEFI?

---

### Post by timbrown527 on 2019-01-04
Well, I think it's the drive. The light on the drive has stopped working. I bet the drive was bad out of the box and just failed.
I'll swap it out tomorrow and get back with further results if any.

---

### Post by QIII on 2019-01-04
Before you do that, what happens if you unplug the drive from its power source and the computer, then plug it back into the computer and reconnect it to its power source?

---

### Post by timbrown527 on 2019-01-04
Already have done that multiple times, on two computers...even using the USB cable from my 1TB drive. Nothing.

---

### Post by QIII on 2019-01-04
Yeah.  I'd say the issue is hardware.

What a pain!

---

### Post by rbmorse on 2019-01-04
I got one of those over the holiday and it did the same thing...lit up/spun up but not recognized by the system, then died all together. Awaiting replacement.

---

### Post by oldfred on 2019-01-04
We have seen multiple cases where newer larger drives do not work with some older external cases or power supplies.

My SSD works with my USB3 cable drawing power from USB port. But it is not enough power to run my older HDD.

---

### Post by timbrown527 on 2019-01-05
Took the drive back to Walmart, exchanged for a Western Digital 4TB passport...the Seagate just felt "cheap". New drive works fine, which is what I would expect. NTFS file system. 

The issue apparently was the drive was bad out of the box.

Thanks for your help!

---

