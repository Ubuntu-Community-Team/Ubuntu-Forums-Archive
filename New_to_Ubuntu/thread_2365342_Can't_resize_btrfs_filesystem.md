---
title: "Can't resize btrfs filesystem"
date: 2017-07-05
forum: New to Ubuntu
---

### Post by mrfrodo2 on 2017-07-05
I have a server with a 30 TB drive attached (target for backups). It filled up and I expanded the device to 40 TB and here is the info on it:

```

sudo lsblk -o NAME,FSTYPE,SIZE,MOUNTPOINT,LABEL,MODEL,HCTL
NAME   FSTYPE  SIZE MOUNTPOINT LABEL MODEL            HCTL
sda             16G                  Virtual disk     32:0:0:0
&#9500;&#9472;sda1 ext4     12G /
&#9500;&#9472;sda2           1K
&#9492;&#9472;sda5 swap      4G [SWAP]
sdb             20G                  Virtual disk     32:0:1:0
sdc           39.5T                  Virtual disk     32:0:2:0
&#9492;&#9472;sdc1 btrfs  26.9T /mnt/sdc1
sr0           1024M                  VMware IDE CDR00 0:0:0:0

```

When I try to resize the sdc1 partition I get the following message:

```
sudo btrfs filesystem resize max /dev/sdc1
ERROR: resize works on mounted filesystems and accepts only
directories as argument. Passing file containing a btrfs image
would resize the underlying filesystem instead of the image.

```

If I try the same command using the mount point I get:

```

sudo btrfs filesystem resize max /mnt/sdc1
Resize '/mnt/sdc1' of 'max'
```

But nothing has changed.

I need to expand the sdc1 partition to use 39.5 TB instead of the current 26.9 TB.

---

### Post by QIII on 2017-07-05
Hello!

Please use code tags around commands issued in the terminal and their results.  This preserves formatting and makes your posts easier to read and understand.

You may use code tags in one of the following ways:

1. Click the # sign above the text input box, place your cursor between the code tags that appear and paste your text.

2. Paste your text, highlight it and click the # sign.

3. Type [noparse]```
[/noparse] before you type or paste your text and [noparse]
```[/noparse] after you type or paste your text. The square brackets are required.

Cheers!

---

### Post by mrfrodo2 on 2017-07-05
Ok, I'll do that in the future.

---

### Post by mrfrodo2 on 2017-07-05
Umm, there is no # sign above the text input box. The only thing that seems close is the "Wrap [QUOTE] tags" button but that doesn't work the same

I guess I can do it the old fashioned way and just type in the code tags.

---

### Post by deadflowr on 2017-07-05
> **mrfrodo2 said:**
> Umm, there is no # sign above the text input box. The only thing that seems close is the "Wrap QUOTE tags" button but that doesn't work the same
Either use the Reply to Thread button or the Go Advanced Button to get the full posting options, the Quick Reply has a limited set of options.
> I guess I can do it the old fashioned way and just type in the code tags.
That also works.

---

### Post by mrfrodo2 on 2017-07-05
I was finally able to expand the partition using partd and then selecting the device, selecting the partition and then resizing the partition. I now see what I expect from lsblk

```

sudo lsblk -o NAME,FSTYPE,SIZE,MOUNTPOINT,LABEL
NAME   FSTYPE  SIZE MOUNTPOINT LABEL
sda             16G
&#9500;&#9472;sda1 ext4     12G /
&#9500;&#9472;sda2           1K
&#9492;&#9472;sda5 swap      4G [SWAP]
sdb             20G
sdc           39.5T
&#9492;&#9472;sdc1 btrfs  39.1T /mnt/sdc1
sr0           1024M

```

However, the space is not showing available to systems trying to write to this server and when I do a df -h I get the following:

```

 df -h
Filesystem      Size  Used Avail Use% Mounted on
udev            7.9G     0  7.9G   0% /dev
tmpfs           1.6G   15M  1.6G   1% /run
/dev/sda1        12G  5.3G  5.9G  48% /
tmpfs           7.9G     0  7.9G   0% /dev/shm
tmpfs           5.0M     0  5.0M   0% /run/lock
tmpfs           7.9G     0  7.9G   0% /sys/fs/cgroup
tmpfs           1.6G     0  1.6G   0% /run/user/1000
/dev/sdc1        27T   25T  2.3T  92% /mnt/sdc1

```

So the space on sdc1 isn't matching up. Any ideas would be helpful.

---

### Post by mrfrodo2 on 2017-07-05
Never mind, I figured it out. After expanding the partition I still had to use the btrfs filesystem resize command to expand the file system to use the full partition.

I'll close the thread.

---

