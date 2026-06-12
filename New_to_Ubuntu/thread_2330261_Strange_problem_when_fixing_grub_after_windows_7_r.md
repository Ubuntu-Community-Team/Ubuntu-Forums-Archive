---
title: "Strange problem when fixing grub after windows 7 re-install"
date: 2016-07-09
forum: New to Ubuntu
---

### Post by Nebelhom on 2016-07-09
Hi Guys,

I have a strange problem to which I could not find a solution. After re-install of Windows 7 thanks to a Windows 10 upgrade that essentially made my PC a random blue screen creator, I now need to fix grub to re-enter my ubuntu partition. I am using ubuntu 14.04.

I tried to follow this thread [http://askubuntu.com/questions/88384/how-can-i-repair-grub-how-to-get-ubuntu-back-after-installing-windows]("http://askubuntu.com/questions/88384/how-can-i-repair-grub-how-to-get-ubuntu-back-after-installing-windows") but for some strange reason I cannot mount the partition that holds the important folders (sda4). Instead I can only mount sda5, a subpart of sda4 containing only a folder named after my username.

If that made little sense, I attached a screenshot of what GParted showed me to make it clearer.

[ATTACH=CONFIG]270043[/ATTACH][ATTACH=CONFIG]270043[/ATTACH]

*_Here are some more details:_*

When I try to run: ```
sudo mount /dev/sda4 /mnt
```

I get ```
mount: you must specify the filesystem type
```

When I mount sda5 and run ```
for i in /sys /proc /run /dev; do sudo mount --bind "$i" "/mnt$i"; done
```

I unsurprisingly get

```
mount: mount point /mnt/sys does not exist
mount: mount point /mnt/proc does not exist
mount: mount point /mnt/run does not exist
mount: mount point /mnt/dev does not exist

```

Since they only exist in sda4 (or ../mnt)

Did anyone of you encounter this problem before and was able to fix it? Any help is highly appreciated. Thanks :)

---

### Post by grahammechanical on 2016-07-09
> but for some strange reason I cannot mount the partition that holds the important folders (sda4).

Do you not mean sda3? The Ubuntu partition is sda3. 

The hard disk has MBR partitioning. That means we are only allowed 4 primary partitions. The work around is to use one of the allocated 4 primary partitions as a special primary partition called an Extended partition and then inside the Extended partition we can create many Logical partitions. Here is your partition layout

Primary partition 1 = sda1 = ntfs = Windows partition
Primary partition 2 = sda2 = ntfs = Windows partition
Primary partition 3 = sda3 = Ext4 = Ubuntu partition
Primary partition 4 = sda4 = Extended partition
Inside sda4 (extended partition)
Logical partition = sda5 = Ext4 Ubuntu home partition
Logical partiton = sda6 = swap partition.

You cannot mount the extended partition (sda4) because it is not a file system. Try again but aim at sda3.

Regards.

---

### Post by Nebelhom on 2016-07-10
@grahammechanical:

*sigh* what can I say? It was late yesterday and I saw sda4 straight away not looking left or right. Now you know why I still put this in "New to Ubuntu" ;)

Thanks a lot! One night and 5 minutes (including boot) later and my grub is working again :)

Is there a way still to mark this thread as solved and give you a +1? I haven't been on the forum in quite some time and it... changed ;)

---

### Post by Nebelhom on 2016-07-10
Nvm, I got the solved bit.

Can't find a +1 for you, sorry :(. Thank you nonetheless!

---

