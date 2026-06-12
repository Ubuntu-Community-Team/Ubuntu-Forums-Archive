---
title: "mount ntfs USB drive"
date: 2020-07-02
forum: New to Ubuntu
---

### Post by optimusprime11 on 2020-07-02
Hey Guys,

I'm struggling a little with the cli. I want to mount a ntfs usb drive so that plex can other system services can read and write to it.

I have edited /etc/fstab with:

"UUID=9C3C7E513C7E2684 /media/usbext ntfs-3g auto,users,uid=1000,gid=1000,dmask=027,fmask=137,utf8 0 0"

I exit nano and type "sudo mount -a" and get no errors.

I then type 'lsblk' and part of the feedback states:
"sda1 8:1 0 5.5T 0 part /media/usbext" (5.5T USB drive mounted to media/usbext)

Looks like i did it? no!

I try and access the directory with:
"cd /media/usbext"

and get:
-bash: cd: /media/usbext: Transport endpoint is not connected

What am I not doing or doing wrong? any help would be really appreciated, please.

Kind Regards,

Chris

---

### Post by TheFu on 2020-07-02
Remove the _dmask=027,fmask=137_ parts.
if you want good options, these are what i use:
```
windows_names,nosuid,noatime,async,big_writes,uid=1000,gid=1000,fmask=0002,dmask=0002
```

That results in expected directory and file permissions.

---

### Post by optimusprime11 on 2020-07-03
Unfortunately no luck, i get the came error output with the following in /etc/fstab:

[UUID=9C3C7E513C7E2684 /media/usbext ntfs-3g [COLOR=#000000][FONT=&quot]windows_names,nosuid,noatime,async,big_writes,uid=1000,gid=1000,fmask=0002,dmask=0002 0 0[/FONT][/COLOR]]

---

### Post by optimusprime11 on 2020-07-03
Hi,

I thought it might be of use to supply the whole contents of /etc/fstab


> /dev/disk/by-uuid/30d530c7-587b-416d-b1c1-6087ffc56a4d / ext4 defaults 0 0 
                                                           /swap.img       none    swap    sw      0       0 
                                                                                   [COLOR=#000000]UUID=9C3C7E513C7E2684 /media/usbext ntfs-3g [/COLOR][COLOR=#000000][COLOR=#000000]windows_names,nosuid,noatime,async,big_writes,uid=1000,gid=1000,fmask=0002,dmask=0002 0 0[/COLOR][/COLOR]    

the first 2 lines "/dev/" and "/swamp.img" were there before I started to edit. I don't think these are having an impact on mounting?

---

### Post by optimusprime11 on 2020-07-03
Here's some more info using "ls -l" and "lsblk". Interesting to see that the permissions cannot be detected with "?". I hope this helps to give us a clue to whats going on? 
Could 'usbmount' be taking preference or conflicting with the info in 'fstab'? 

> [COLOR=#ff0000]chris@server:/media$ ls -l [/COLOR]
                                                                                             ls: cannot access 'usbext': Transport endpoint is not connected 
                                                        total 32 
                                                                                                               lrwxrwxrwx 1 root root    4 Jul  1 12:59 usb -> usb0 
                                                                   drwxr-xr-x 2 root root 4096 Jul  1 12:59 usb0 
                                                                          drwxr-xr-x 2 root root 4096 Jul  1 12:59 usb1 
                                                                          drwxr-xr-x 2 root root 4096 Jul  1 12:59 usb2 
                                                                          drwxr-xr-x 2 root root 4096 Jul  1 12:59 usb3 
                                                                          drwxr-xr-x 2 root root 4096 Jul  1 12:59 usb4 
                                                                          drwxr-xr-x 2 root root 4096 Jul  1 12:59 usb5 
                                                                          drwxr-xr-x 2 root root 4096 Jul  1 12:59 usb6 
                                                                          drwxr-xr-x 2 root root 4096 Jul  1 12:59 usb7 
                                                                          d????????? ? ?    ?       ?            ?usbext 
                                                                        [COLOR=#ff0000]chris@server:/media$ lsblk [/COLOR]
                                                                                             NAME        MAJ:MIN RM   SIZE RO TYPE MOUNTPOINT 
                                                                       loop0         7:0    0    55M  1 loop /snap/core18/1705 
                                                                loop1         7:1    0    55M  1 loop /snap/core18/1754
loop2         7:2    0  71.2M  1 loop /snap/lxd/15896 
                                                                  loop3         7:3    0  71.2M  1 loop /snap/lxd/15913 
                                                                  loop4         7:4    0  29.8M  1 loop /snap/snapd/
8140                                                                  loop5         7:5    0  27.1M  1 loop /snap/snapd/
7264                                                                  sda           8:0    0   5.5T  0 disk 
                                                                                  &#9492;&#9472;sda1        8:1    0   5.5T  0 part /media/usbext 
                                                                    sdb           8:16   0 119.2G  0 disk 
                                                                                  &#9500;&#9472;sdb1        8:17   0 118.7G  0 part 
                                                                                  &#9492;&#9472;sdb2        8:18   0   615M  0 part 
                                                                                  nvme0n1     259:0    0 232.9G  0 disk 
                                                                                  &#9500;&#9472;nvme0n1p1 259:1    0     1M  0 part 
                                                                                  &#9492;&#9472;nvme0n1p2 259:2    0 232.9G  0 part /   

---

### Post by optimusprime11 on 2020-07-03
I edited > sudo nano /etc/usbmount/usbmount.conf to disable it (setting 0). I rebooted the machine and it works! problem is (I assume) if I insert a USB drive it wouldn't automatically mount for access?

Sorry for the many posts, it helps me keep a log of what i'm doing and hopefully tells you where i'm going with this.

---

### Post by ActionParsnip on 2020-07-03
If its NTFS, also run a full chkdsk in Windows on the drive to make sure the file system is complete and consistent

---

### Post by TheFu on 2020-07-03
```
UUID=9C3C7E513C7E2684 /media/usbext ntfs-3g windows_names,nosuid,noatime,async,big_writes,[COLOR="#FF0000"]uid= 1000[/COLOR],gid=1000,fmask=0002,dmask=0002 0 0
```

[LIST]
[*]Is showing a space in between some options. No spaces are allowed.
[*]The UUID must be correct, if you use UUIDs for the mount.  **blkid** is the command to see that.  Or you can use the file system LABEL, if one has been set and is unique.  I use LABEL=250G in one mount, for example.
[*]The /media/usbext directory shouldn't need to exist now that systemd-mount has taken over the fstab, but it wouldn't hurt to create it. **sudo mkdir /media/usbext**
[*] ntfs-3g and ntfs for the type of file system shouldn't make any difference. Both are acceptable. I've used just ntfs for years.
[*] If the HDD was connected to Windows recently, that other OS may have not properly closed the file system. Unfortunately, the only solution for that is to connect to it Windows, run scandisk and chkdsk (however they are spelled), then disable hibernation in Windows and use the "eject" option so that Windows will properly close the file system.  MSFT started doing this from Win8 and later.
[/LIST]

That's all I got.  I've never seen a refusal to mount, but I do see NTFS corruption about once a month on my single NTFS HDD here. Just yesterday, I had to wipe and reformat that disk because some zero-length files showed up that couldn't be removed. My NTFS disk is used by a video recording device that only works with NTFS or FAT32.

---

### Post by optimusprime11 on 2020-07-14
Update: I unfortunately had to restart the server from scratch but that&#8217;s bound to happen a few times while I&#8217;m learning. I found that usbmount conflicts with mounting of a drive configured via /etc/fstab. No idea why but I don&#8217;t need usbmount so I worked around it.
thank you for your help.

---

