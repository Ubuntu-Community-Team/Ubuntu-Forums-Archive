---
title: "Partitions stopped mounting automatically"
date: 2018-03-04
forum: New to Ubuntu
---

### Post by tart1988 on 2018-03-04
I am using Ubuntu 16.04. I did something with it and now, when I reboot, the partitions are not mounted automatically. Only / , /boot/efi/ and swap are mounted and only they are contained in the fstab file. The other five are not. When I open nautilus I see all partitions and can mount them by clicking on their icons. The strange thing is that gnome-disks shows that all partitions should be mounted at startup. Why are they not then? Or are they mounted first and then, for some reason, are immediately unmounted? The only suspicious thing which I found in dmesg reads

*EXT4-fs (sda3): re-mounted. Opts: errors=remount-ro*

I don't want just to edit the fstab file. I want to understand the reason why this is happening. I am new to Ubuntu. :confused:

**EDIT:**

I suspect that the issue was caused by **ddrescue**. Here is the logfile:

```

# Rescue Logfile. Created by GNU ddrescue version 1.19
# Command line: ddrescue -f -r3 /dev/sdc1 /dev/sdb4 logfile
# Start time:   2018-03-04 01:39:04
# Current time: 2018-03-04 01:41:40
# Finished
# current_pos  current_status
0x102FBE00     +
#      pos        size  status
0x00000000  0x102BC000  +
0x102BC000  0x00040000  -
0x102FC000  0x2D100000  +

```

*/dev/sdc1* was the corrupt flash drive files from which I wanted to recover. I think that after I ran **ddrescue **my drives became unmounted and stopped mounting at startup. Could this happen?

---

### Post by deadflowr on 2018-03-04
In Disks (gnome-disks) is Automatic Mount Options at the top toggle to On or Off?

---

### Post by tart1988 on 2018-03-05
[COLOR=#000000]Automatic Mount Options are On for [/COLOR][COLOR=#000000]exactly [/COLOR][COLOR=#000000]those partitions which do not mount. They are Off for the partitions which do mount. [/COLOR]

---

### Post by Morbius1 on 2018-03-05
Why not just post the output of the following commands so the folks here can help you:
```
sudo blkid -c /dev/null -o list
```
```
cat /etc/fstab
```

---

### Post by tart1988 on 2018-03-05
> [COLOR=#000000][FONT=Ubuntu Mono]sudo blkid -c /dev/null -o list[/FONT][/COLOR] returns

```

device     fs_type label    mount point    UUID
-------------------------------------------------------------------------------
/dev/loop0 squashfs         /snap/core/4017 
/dev/loop1 squashfs         /snap/core/3887 
/dev/loop2 squashfs         /snap/core/4110 
/dev/sda1  vfat    ESP      /boot/efi      0AEC-8283
/dev/sda2  vfat    OS       (not mounted)  6810-7989
/dev/sda3  ext4    UBUNTU   /              64ef968d-8488-49b1-8dde-a0829168b76f
/dev/sda4  swap             [SWAP]         181a3feb-93f6-4e98-8583-52a683f658bc
/dev/sdb1  ntfs    C        (not mounted)  16D1E84B6E1AEFF3
/dev/sdb2  ntfs    D        (not mounted)  329D74C657FEB321
/dev/sdb3  ntfs    F        (not mounted)  4E0068F541357DFD
/dev/sdb4  vfat    G        (not mounted)  FB47-7552

```

> [COLOR=#000000][FONT=Ubuntu Mono]cat /etc/fstab[/FONT][/COLOR] returns

```

# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda3 during installation
UUID=64ef968d-8488-49b1-8dde-a0829168b76f /               ext4    errors=remount-ro 0       1
# /boot/efi was on /dev/sda1 during installation
UUID=0AEC-8283  /boot/efi       vfat    umask=0077      0       1
# swap was on /dev/sda4 during installation
UUID=181a3feb-93f6-4e98-8583-52a683f658bc none            swap    sw              0       0

```

---

### Post by Morbius1 on 2018-03-05
In your very first post you present a paradox:
> I don't want just to edit the fstab file. I want to understand the reason why this is happening.
The people here who can provide you with the assistance you need to mount your partitions at boot do not use Disks.

---

### Post by tart1988 on 2018-03-05
> [COLOR=#000000]The people here who can provide you with the assistance you need to mount your partitions at boot do not use Disks.[/COLOR]
That's OK.

---

### Post by Morbius1 on 2018-03-05
If it were me I'm a firm believer in templates when it comes to fstab. Like the ones the Ubuntu installer uses when you select "Something Else".

An example of an NTFS template would be something like this - and I will base it on the data provided for your "D Drive":
```
UUID=329D74C657FEB321 /media/WinD ntfs defaults,nls=utf8,uid=1000,umask=0000,windows_names 0 0
```

Notes:

[1] You will need to create the mount point yourself:
```
sudo mkdir /media/WinD
```

[COLOR=#0000cd][I]With a mount point under /media the mounted partition will show up on the side panel of your file manager and other places. If you don't want that to happen create the mount point under /mnt - as in /mnt/WinD. 

[/I][/COLOR][2] **uid=1000** will make you the owner of the mounted partition.

[COLOR=#0000cd]*To verify that is your uid number run this command:*[/COLOR]
```
id
```

[3] **umask=0000 **will make the permissions of the mounted partition 777 - which it will do by default but I place it there if I want to change things later on.

[COLOR=#0000cd][I]For example: If I want to make it so only I have access to the partition then I would change the umask value to 0077.

[/I][/COLOR][COLOR=#000000][4] **windows_names** will prevent you from saving a file in Linux with a name that contains characters Windows cannot interpret.

None of the options I presented above are available in Disks by default. You can always force it to those options in Disks but then why use Disks in the first place.[/COLOR]

---

### Post by tart1988 on 2018-03-05
Thank you very much for explaining these parameters. I will take note of them. Your explanations are very informative and helpful. 

However, I would really like to understand why that thing happened in the first place. Is the fstab file, which I copied above, not the default fstab file shipped with Ubuntu 16.04? If memory serves, when I just bought the laptop, I couldn't see my HDD (/*dev/sda*'s are on SSD, */dev/sdb*'s are on HDD). Then I partitioned it using Disks or **gparted** and everything worked fine since then. I don't remember editing fstab file or even changing any parameters in Disks. Apart from **ddrescue**, I also ran **foremost** on that night, but I think the problem appeared after **ddrescue**. ```
[COLOR=#000000][FONT=Ubuntu Mono]ddrescue -f -r3 /dev/sdc1 /dev/sdb4 logfile[/FONT][/COLOR]
```
did repartition [COLOR=#000000][FONT=Ubuntu Mono]*/dev/sdb4*. [/FONT][/COLOR]Perhaps, it did more, but what?

---

