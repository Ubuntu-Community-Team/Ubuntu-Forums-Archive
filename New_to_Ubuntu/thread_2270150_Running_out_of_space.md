---
title: "Running out of space"
date: 2015-03-20
forum: New to Ubuntu
---

### Post by ariel6 on 2015-03-20
Hello everyone,

I have an the root partition of 20gb and the rest for home. As I have 24GB of memory ram I don't have swap but the thing is that as I have almos root full, when I load an online hd move I start getting a warning message saying that I am running out of space. I check the memory usage and it does not change at all/ What should I do so the movie is loaded on RAM rather than /root?

Thank you very much for any kind of information/help.

---

### Post by v3.xx on 2015-03-20
> I have an the root partition of 20gb and the rest for home.
The rest of what for home?  Are you running a separate home partition?

Please post the output of
```
df -h
```
[https://help.ubuntu.com/community/UsingTheTerminal#Starting_a_Terminal](https://help.ubuntu.com/community/UsingTheTerminal#Starting_a_Terminal)

---

### Post by ariel6 on 2015-03-20
I should have been more clear.
I have two ssd drives in raid 0 where I have two partitions. One for windows (236 GB) and a small one for ubuntu (20gb). And I have a hdd with other two partitions, a big one 800GB ntfs and a 100gb ext4 for /home.

The output of df -h is:

Filesystem                                  Size  Used Avail Use% Mounted on
/dev/mapper/isw_dfhfgbggca_RAID0IMSVolume5   20G   19G  540M  98% /
udev                                         12G  4.0K   12G   1% /dev
tmpfs                                       2.4G  888K  2.4G   1% /run
none                                        5.0M     0  5.0M   0% /run/lock
none                                         12G  848K   12G   1% /run/shm
/dev/mapper/isw_dfhfgbggca_RAID0IMSVolume2  296M   52M  245M  18% /boot/efi
/dev/sdc3                                    99G   35G   60G  37% /home

---

### Post by SeijiSensei on 2015-03-20
The usual candidates are /var/log and /var/cache/apt/archives. Run "du -s /var/log" and "du -s /var/cache/apt" and see how big they are.  If that doesn't help, try this:
```

cd  /
sudo du -sx *

```
(The "x" switch limits du to a single file system, in this case the root file system.)

One possibility is that there is something in the actual /home directory in the root filesystem.  Try rebooting into "recovery mode" then unmount /home and see if /home is really empty.  Once you mount the other filesystem into /home, it will hide anything in the original /home directory.

---

### Post by v3.xx on 2015-03-20
SeijiSensei's got it :)

---

### Post by ariel6 on 2015-03-21
> **SeijiSensei said:**
> The usual candidates are /var/log and /var/cache/apt/archives. Run "du -s /var/log" and "du -s /var/cache/apt" and see how big they are.  If that doesn't help, try this:
```

cd  /
sudo du -sx *

```
(The "x" switch limits du to a single file system, in this case the root file system.)

One possibility is that there is something in the actual /home directory in the root filesystem.  Try rebooting into "recovery mode" then unmount /home and see if /home is really empty.  Once you mount the other filesystem into /home, it will hide anything in the original /home directory.

I'm sorry but I don't follow you when you said to mount the other filesystem into /home. What other filesystem? In case you meant windows, I should have said that I don't use it at all :). Just don't want to delete it for now.

---

### Post by Holger_Gehrke on 2015-03-21
> **ariel6 said:**
> I'm sorry but I don't follow you when you said to mount the other filesystem into /home. What other filesystem? In case you meant windows, I should have said that I don't use it at all :). Just don't want to delete it for now.

The one you normally mount into /home, the one on /dev/sdc3. When you mount a file system into a directory, the files which are in that directory become inaccessible and basically invisible but still take up space. It's rather unlikely that that's the cause, but it's not impossible. If you set up the system with /home as a partition of it's own when installing there should not be any files in the directory /home on the root partition. But if you set it up that way after installation, you might have used /home for a while as a normal directory and there might be some left over files in there.

Personally, I think '/var/cache/apt/archives is the most likely culprit; all packages you've installed and all updates are stored there and unless one runs 'sudo apt-get clean' or 'sudo apt-get autoclean' they stay there.

---

### Post by sotiris2 on 2015-03-21
You have a root filesystem which has a folder named home. You mount another filesystem (on the HD) to that folder. 

Normally the actual folder home on the root filesystem will be empty. But if it isn't it does not prevent you from mounting another filesystem there, hiding whatever is there. 

Now why would your /home folder on the root partition not be empty if you use an extra partition? In case you didn't originally have a different partition for home but created later (and failed to delete the contents of the original folder). Maybe if the hard drive wasn't accessible to be mounted and you still logged in somehow (don't think gui would work though). 

He didn't tell you to mount but rather to UNmount the filesystem from /home, in recovery mode and check if it's empty. To accomplish this

Reboot to recovery mode. Select advanced option on the grub menu and then recovery mode. If you don't get a grub menu on boot hold shift while booting. 

In recovery select root. When you get to a command prompt type: ```
mount
``` Find out what is the "name" of the partition mounted on /home. It will be of the form /dev/sdx#. x is a letter, # a number. Keep in mind sdx# and type ```
umount /dev/sdx#
``` Remember to replace x and # with the correct letter and number. If you don't get an error type ```
ls -A
``` Which should come up empty, if umount succeded. 

Keep it mind though that is the less likely problem so you should check the logs as instructed.

---

### Post by Impavidus on 2015-03-21
IIRC, in recovery mode only the root file system is mounted automatically (and some pseudo-filesystems, of course). No need to unmount anything before checking.

BTW, here is a guide with general tricks to find your lost disk space: [http://ubuntuforums.org/showthread.php?t=1122670](http://ubuntuforums.org/showthread.php?t=1122670)

---

### Post by Dina_Eaton on 2015-03-21
Maybe you have some old Kernels still on disk, if you've had it for a long time.

---

### Post by ariel6 on 2015-03-21
> **Impavidus said:**
> IIRC, in recovery mode only the root file system is mounted automatically (and some pseudo-filesystems, of course). No need to unmount anything before checking.

BTW, here is a guide with general tricks to find your lost disk space: [http://ubuntuforums.org/showthread.php?t=1122670](http://ubuntuforums.org/showthread.php?t=1122670)

I will follow this guide. Thanks for sharing it.

But just one thing. When I installed ubuntu I chose the other partition for /home so that should be correct. And the issue here isn't it why when I load a move online for example it is not loaded on RAM rather on /root?

Thanks again for the bit help to everyone!

---

### Post by Holger_Gehrke on 2015-03-21
The program you're using probably was written with the more normal situation of scarce ram and plenty of hd space in mind. It probably writes temporary data to /tmp. Setting up a tmpfs - a dynamic ram disk - and mounting that as /tmp may help in your situation.

---

### Post by ariel6 on 2015-03-21
I'm using firefox for this....

I have been loading a movie while getting the warning message and also checking /tmp with du -hs /tmp and I only saw a change from 44K to 84K, but the warning went from 1GB left to 584MB, so /tmp does not seem to be the problem.

---

### Post by Holger_Gehrke on 2015-03-21
Thank you for giving me this opportunity to learn something new ! :p
I looked at the output of 'lsof -c firefox' while playing a video on youtube and found that firefox does indeed have a temporary file in /tmp:
```

firefox 3475 holgeh   60u   REG        8,3  9240576 6827445 /tmp/mozilla-temp-1127485724 (deleted)

```
A minute or two later
```

firefox 3475 holgeh   60u   REG        8,3 31916032 6827445 /tmp/mozilla-temp-1127485724 (deleted)

```

As you can see, the file is marked as deleted. This seems to be a trick to stop people from messing with the temporary file while it's in use; you create the file, open it for reading and writing, keep the file open but delete it. As long as you don't close the file it's still accessible but doesn't show up in 'ls' or other tools to examine the filesystem. This was only a 9 minute low resolution video clip. If it was a full high resolution movie, the file would probably be a lot bigger ...

---

### Post by ariel6 on 2015-03-22
> **Holger_Gehrke said:**
> Thank you for giving me this opportunity to learn something new ! :p
I looked at the output of 'lsof -c firefox' while playing a video on youtube and found that firefox does indeed have a temporary file in /tmp:
```

firefox 3475 holgeh   60u   REG        8,3  9240576 6827445 /tmp/mozilla-temp-1127485724 (deleted)

```
A minute or two later
```

firefox 3475 holgeh   60u   REG        8,3 31916032 6827445 /tmp/mozilla-temp-1127485724 (deleted)

```

As you can see, the file is marked as deleted. This seems to be a trick to stop people from messing with the temporary file while it's in use; you create the file, open it for reading and writing, keep the file open but delete it. As long as you don't close the file it's still accessible but doesn't show up in 'ls' or other tools to examine the filesystem. This was only a 9 minute low resolution video clip. If it was a full high resolution movie, the file would probably be a lot bigger ...

With that in mind and > **Holger_Gehrke said:**
> The program you're using probably was  written with the more normal situation of scarce ram and plenty of hd  space in mind. It probably writes temporary data to /tmp. Setting up a  tmpfs - a dynamic ram disk - and mounting that as /tmp may help in your  situation.
I included in in /etc/fstab
```
tmpfs /tmp tmpfs defaults,noatime,nosuid,nodev,noexec,mode=1777,size=512M 0 0
```


And now I didn't get the warning message. I have been monitorin the RAM with the app "system monitor" and it went from 1.5GB to 2.2GB, but it seems that there is a limit and if I want to load another large video from a different website for example, it just doesn't load. Could that be related to some sort of 'limit' or something like that?

---

### Post by Holger_Gehrke on 2015-03-22
The option 'size' is an upper limit for the amount of RAM tmpfs is allowed to use. without that option, tmpfs defaults to using 50% of RAM maximum. tmpfs only uses as much ram (up to the given limit) as is needed for the stored files and their metadata.

---

### Post by ariel6 on 2015-03-22
So instead of```
tmpfs /tmp tmpfs defaults,noatime,nosuid,nodev,noexec,mode=1777,size=512M 0 0
``` it should be something like ```
tmpfs /tmp tmpfs defaults,noatime,nosuid,nodev,noexec,mode=1777,size=2G 0 0
``` for example? 

When you say 50% of ram, is it 50% of the value set to size or the actual ram memory? If it is the second option is strange because I have 24GB...

---

### Post by Holger_Gehrke on 2015-03-22
If you **don't** give it a size parameter, it uses the default of (up to) 50% of RAM. If you do give a size, it uses that, maximally. The size value can be either an absolute value with a suffix of 'M' or 'G' for Megabyte or Gigabyte or a percentage of total RAM with a suffix of '%'.

---

### Post by ariel6 on 2015-03-23
> **Holger_Gehrke said:**
> If you **don't** give it a size parameter, it uses the default of (up to) 50% of RAM. If you do give a size, it uses that, maximally. The size value can be either an absolute value with a suffix of 'M' or 'G' for Megabyte or Gigabyte or a percentage of total RAM with a suffix of '%'.

Ok, I removed the size parameter and when I loaded a movie I didn't get any warning message. I guess the 'problem' is solved. Thank you everyone for the help!

---

