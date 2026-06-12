---
title: "Misunderstanding /etc/fstab?"
date: 2012-09-19
forum: New to Ubuntu
---

### Post by foberle on 2012-09-19
I have a dual boot machine (Windows and recently installed Ubuntu 12.04) with several logical drives (formatted as ntfs) that I want to access in Ubuntu. When I use Nautilus, these all show up as “Devices” at the top of the left hand panel. When I select them, they are apparently automatically mounted, and an icon for the drive then appears in the left hand launcher panel of the desktop.
 

 When I choose to [Restart] or [Shut Down], these “devices” seem to be automatically unmounted, and I can also manually unmount them by clicking on the button next to the drive name in Nautilus.
 

 For various reasons, I wanted to have a few of these drives mount at startup, and I found many recommendations on how to add entries to /etc/fstab to do this. For example, I added the following lines to the file by “sudo gedit /etc/fstab”: …
 

 ```
/dev/sda5         /media/Development     ntfs    rw,user,auto        0       0
 /dev/sda7         /media/Genealogy         ntfs    rw,user,auto        0       0 
``` 
 

 … and the devices were indeed mounted at startup, and showed up in Nautilus with the “unmount” icon next to them as expected. So far, so good.
 

 What I didn't expect was that, on shutdown, Ubuntu would almost shut down, but then “hang” after the desktop was long gone with only the text “Ubuntu” displayed in the center of the screen. I guessed (and this seems to be correct) that nothing was telling the drives to unmount automatically. So I powered off with the machine's reset button and rebooted.
 

 Everything started nicely again, and I attempted to use the “unmount” icons in both Nautilus and the launcher panel before shutting down again, but was told that only root had permission to do this. Argghhh.
 

 So, I used “sudo umount /dev/sda5” and “sudo umount /dev/sda7” and was then able to shut down normally without any hang-up.
 

 So what magic option do I need to use to “cure” this user-hostile behavior? Do I need to have a user-only set of mount options that I have permission to unmount and, if so, how do I do that? I tried editing the /etc/fstab without sudo, but it won't permit me to save it.
 

 Also, I really don't want the icons for these drives/devices or whatever to appear in the launcher panel, as they just take up space – it also seems less than useful to have them there since they look exactly alike and, with the need to poke the mouse around a fair bit to get the little call-outs to display that tell you what the icon represents (I presume that's a bug of some sort in Unity), these icons are not very useful. Is there a way to keep them from showing up in the launcher?
 

 What I would really like is to have the drives I choose simply appear without any fuss under the section titled “Computer” (where the entries are Home, Desktop, Documents, and so forth). Can I simply have (for instance) my Genealogy partition (see sda7 above) appear in the list under Computer instead of Devices? I want them to feel like they're part of the family rather than being treated like lowly USB sticks :)!
 

 One other thing (is this too many questions in one post?). Not unexpectedly, the partition that is the c:\ drive in Windows appears under Devices in Navigator. Is there a way to “hide” this to avoid inadvertently disturbing any files there, since all of my “data” files are located in other partitions?
 

 Thanks in advance for any suggestions ...

---

### Post by oldfred on 2012-09-19
I am not running Unity so I do not understand those issues.

You are mounting in /media. Any mounts in /media & /home will show in Naulitus' left panel. If you do not want those mounts you can mount in / (root) or mount in /mnt. I mount my shared NTFS data partition in /mnt/shared and link folders in the shared into my /home. Then it is in /home but not in Nautilus. 

Understanding fstab
[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)
[https://help.ubuntu.com/community/Mount/](https://help.ubuntu.com/community/Mount/)
[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)

Ownership and permissions of vfat / ntfs are set at the time of mounting. This is often a source of confusion.
HOWTO: Mount NTFS partitions with specific ownership/permissions - WorMzy
[http://ubuntuforums.org/showthread.php?t=1604251](http://ubuntuforums.org/showthread.php?t=1604251)
[http://www.psychocats.net/ubuntu/mountwindowsfstab](http://www.psychocats.net/ubuntu/mountwindowsfstab)

[http://ubuntuforums.org/showthread.php?t=1983336](http://ubuntuforums.org/showthread.php?t=1983336)
suggest using templates instead. Post #6
For ntfs UUID shown is example only see below:
UUID=DA9056C19056A3B3 /media/WinD ntfs defaults,nls=utf8,umask=000,uid=1000,windows_names 0 0
Window_names prevents the use of invalid windows characters:
(which are the nine characters ” * / : < > ? \ | and those whose code is less than 0×20) 
uid=1000 should fix the trash problems as well:

For ext4:
UUID=076426af-cbc5-4966-8cd4-af0f5c879646 /media/Data ext4 defaults,noatime 0 2
** To find the correct UUID for your partitions:
sudo blkid -c /dev/null -o list
** You will have to create the mount point yourself, for example:
sudo mkdir /media/WinD
and/or 
sudo mkdir /media/Data
** Then add the template with the correct UUID and mount point to fstab:
sudo cp /etc/fstab /etc/fstab.backup
gksu gedit /etc/fstab
** And when you are done editing fstab and saving it run the following command to test for errors and mount the partitions without requiring a reboot. You will know before you reboot if something is amiss. :
sudo mount -a

Hide mount change UUID to your partition:
sudo mkdir /mnt/SysRes
UUID=200C11850C1156DE /mnt/SysRes ntfs defaults,noauto 0 0
Hide windows mount with noauto: 777 is no permissions at all
/dev/sda2 /Windows/sda2 ntfs defaults,noauto,umask=777 0 0

Set windows boot partition Read only - Morbius1
[http://ubuntuforums.org/showthread.php?t=2043862:](http://ubuntuforums.org/showthread.php?t=2043862:)
After Ubuntu has done it's thing I usually go in and change the umask to 227 which will make the C Drive read only.
/dev/sda1 /media/sda1 ntfs nls=iso8859-1,ro,umask=227 0 0 
UUID=xxxxxxxxxxxxxxx /WinC ntfs defaults,noauto,ro,umask=227 0 0

Mount in /media or /home will show in Nautilus left panel mounts in / or /mnt will not.

---

### Post by foberle on 2012-09-21
Thanks for all the references Fred....

After digging through all of them, I was finally able to come up with something like I wanted to achieve.

---

### Post by oldfred on 2012-09-21
Glad it worked.

Sometimes it is a lot of info, but I rather give to much for those who may be interested. Sometimes just seeing the same info a couple of different ways also makes more sense.

---

