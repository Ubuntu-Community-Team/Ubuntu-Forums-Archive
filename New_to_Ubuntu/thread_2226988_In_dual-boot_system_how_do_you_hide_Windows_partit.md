---
title: "In dual-boot system how do you hide Windows partitions in PCManFM?"
date: 2014-05-30
forum: New to Ubuntu
---

### Post by twalp on 2014-05-30
The dual-boot system I'm working on can boot to Windows 7 and Lubuntu. There's also a "Data" partition on the drive for Windows. When I open PCManFM in Lubuntu the Windows 7 partition and it NTFS "Data" partition are visible. I don't want the end-user of Lubuntu to have access to those two Windows-related partitions (highlighted below). 

[IMG]http://imageshack.com/a/img842/8089/yjd4.png[/IMG]

I found a thread at StackExchange that describes how to hide them but it was valid up to Lubuntu 13.04, so I figure some detail might have changed. Or, for all I know these instructions could be invalid or not the best solution.

In brief, the steps from that post are (and please note that I am a keyboard monkey with this stuff, knowing next-to-nothing about Linux):
```
sudo blkid

/dev/sda3: LABEL="WIN-NTFS1" UUID="1F297ED5220E41AA" TYPE="ntfs"
/dev/sda4: LABEL="WIN-NTFS2" UUID="4CFEB84C16B24904" TYPE="ntfs"
```

Write down the above device info for the NTFS drives to be hidden. 

Create a udev rule.

```
sudo nano /etc/udev/rules.d/99-hide-ntfs-partitions.rules
KERNEL=="sda3", ENV{UDISKS_IGNORE}="1"
KERNEL=="sda4", ENV{UDISKS_IGNORE}="1"
```

Save the changes in Nano.

Refresh the udev rules with:
```
sudo udevadm trigger
```

**Please tell me if the above instructions are the best way to prevent PCManFM from displaying the Windows partitions.  Thank you.**

---

### Post by oldfred on 2014-05-30
I have not seen those directions, as udev is the auto mount option.

I have seen settings in fstab. You actually mount it and make it inaccessible.

         [http://ubuntuforums.org/showthread.php?t=1983336](http://ubuntuforums.org/showthread.php?t=1983336)
Mount & edit fstab from user Morbius1 in Post # 6 - suggest using templates instead.

Some examples, use your UUIDs & mount points:
Hide mount 
UUID=200C11850C1156DE /mnt/SysRes ntfs defaults,noauto 0 0
Hide windows mount with noauto: 777 is no permissions at all
/dev/sda2 /Windows/sda2 ntfs defaults,noauto,umask=777 0 0
sudo mkdir /mnt/SysRes
#hide windows 7 second hard drive
UUID=8A4029F24029E5A3 /mnt/reserved ntfs defaults,noauto 0 0
UUID=80A02B83A02B7F32 /mnt/win7 ntfs defaults,noauto,umask=777 0 0

---

### Post by twalp on 2014-05-30
Wow, 91 views and not one reply? Surely there's a Lubuntu pro around here somewhere! I'd simply try the code but would hate to pooch the system experimenting.

---

### Post by twalp on 2014-05-30
> **oldfred said:**
> I have not seen those directions, as udev is the auto mount option.

I have seen settings in fstab. You actually mount it and make it inaccessible.

         [http://ubuntuforums.org/showthread.php?t=1983336](http://ubuntuforums.org/showthread.php?t=1983336)
Mount & edit fstab from user Morbius1 in Post # 6 - suggest using templates instead.

Some examples, use your UUIDs & mount points:
Hide mount 
UUID=200C11850C1156DE /mnt/SysRes ntfs defaults,noauto 0 0
Hide windows mount with noauto: 777 is no permissions at all
/dev/sda2 /Windows/sda2 ntfs defaults,noauto,umask=777 0 0
sudo mkdir /mnt/SysRes
#hide windows 7 second hard drive
UUID=8A4029F24029E5A3 /mnt/reserved ntfs defaults,noauto 0 0
UUID=80A02B83A02B7F32 /mnt/win7 ntfs defaults,noauto,umask=777 0 0

(timing is everything) Thank you for replying, oldfred.  I'll study your post. It sounds a little over my head ("use templates" sounds easy except to someone who has no idea what templates are in this context, much less how to "use" them) but I'll dig in nonetheless.

---

### Post by oldfred on 2014-05-30
You can just copy & paste template into fstab and edit with your UUID from sudo blkid and your mount point which you must create. Shows how in link, if not sure.
And the examples are just the templates you may want.

And run this afterwards as it will verify fstab works if no errors or give you messages if something does not mount correctly. And then your Windows should disappear. Make sure you have unmounted if you used Nautilus to mount first.
       sudo mount -a

---

### Post by newbie2244 on 2014-05-31
This link [http://ubuntuforums.org/showthread.php?t=2222410&highlight=editing+Places](http://ubuntuforums.org/showthread.php?t=2222410&highlight=editing+Places)   may be helpful.

---

### Post by twalp on 2014-06-01
> **newbie2244 said:**
> This link [http://ubuntuforums.org/showthread.php?t=2222410&highlight=editing+Places](http://ubuntuforums.org/showthread.php?t=2222410&highlight=editing+Places)   may be helpful.

Thank you for trying to help, newbie2244, but it looks like the link you cite applies to Nautilus instead of PCManFM.  Please correct me if I'm wrong.

---

### Post by Morbius1 on 2014-06-01
You've provided everything in your posts you need to prevent the mounting of these partitions:
> sudo blkid

/dev/sda3: LABEL="WIN-NTFS1" UUID="1F297ED5220E41AA" TYPE="ntfs"
/dev/sda4: LABEL="WIN-NTFS2" UUID="4CFEB84C16B24904" TYPE="ntfs"

[1] Create the mount point:
```
sudo mkdir /mnt/WIN-NTFS1
```
[2] Add a line to the end of /etc/fstab:
```
UUID=1F297ED5220E41AA /mnt/WIN-NTFS1 ntfs defaults,noauto 0 0
```

Do the same type of thing for the other ntfs partition except for a new mount point /mnt/WIN-NTFS2 and its UUID.

---

### Post by newbie2244 on 2014-06-01
Twalp -- 

The link was supposed to suggest [ operative phrase "may be helpful"] - not answer directly - a possible way to proceed. I read the docs on PCManFm. My answer was based on Nautilus and PCManFm.  If what you want is an immediate unequivocal answer, get paid tech support.

---

### Post by twalp on 2014-06-10
> **Morbius1 said:**
> You've provided everything in your posts you need to prevent the mounting of these partitions:


[1] Create the mount point:
```
sudo mkdir /mnt/WIN-NTFS1
```
[2] Add a line to the end of /etc/fstab:
```
UUID=1F297ED5220E41AA /mnt/WIN-NTFS1 ntfs defaults,noauto 0 0
```

Do the same type of thing for the other ntfs partition except for a new mount point /mnt/WIN-NTFS2 and its UUID.

Thank you Morbius1 (and oldfred and newbie2244) for replying, and particularly Morbius1's hint that all the answers were within his reply. I'm such a lowly noob that I had to learn how to execute each step, especially how to add the lines to the end of /etc/fstab. 

I succeeded! (and wouldn't have without your help)

---

