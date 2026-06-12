---
title: "Synology Drive open files"
date: 2021-02-08
forum: New to Ubuntu
---

### Post by paullangdon678 on 2021-02-08
Hi I have my Ubuntu working quite nicely but have a question about files on a shared hard drive. I can see the files on this drive but I cannot open them.
I have attached a screenshot of the hard drive contents which are synched from a Synology NAS.
I would be grateful for advice - the message I get when trying to open is 'Could not display - there is no application installed for symbolic link files'. The files are downloaded though.
I am on Ubuntu 20.04.

---

### Post by TheFu on 2021-02-11
Permissions?
Text-only please.  [https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)

---

### Post by paullangdon678 on 2021-02-15
Yes thanks I am having a look at that. I am wondering if the Synology on demand might be part of the issue. I can see and use what must be the NAS network locations fine.

---

### Post by Holger_Gehrke on 2021-02-15
From the error message and the iconography in the image I believe the files you're trying to access are actually symbolic links to files which have been moved or deleted since those links were created. Or it could be a link pointing to files on a shared network location which isn't currently mounted.

Holger

---

### Post by paullangdon678 on 2021-03-04
> **Holger_Gehrke said:**
> From the error message and the iconography in the image I believe the files you're trying to access are actually symbolic links to files which have been moved or deleted since those links were created. Or it could be a link pointing to files on a shared network location which isn't currently mounted.

Holger

Yes sorry the delay in coming back to you - I have been working reading through an Ubuntu unleashed book to get a bit more up to speed. You are probably right as I can create files within a different folder and open them fine. 

Also have four network locations which all have Synology in their title and all appear to contain the same material in a folder called Drive, as I have on the Toshiba storage drive which is the one I expected to see and it set to synchronise with my Synology NAS.

Other files can be opened on all locations and folders except the Synology Drive on on the Toshiba Drive (i.e. the one that is synched).

A general explanation on my structure which I do not yet understand might be helpful but I think the main question I need an answer to is how do I mount the shared network location. The fact that network locations appear suggests they are mounted? 

I hope this makes sense - I am getting a little lost with this.

---

### Post by TheFu on 2021-03-04
Don't use the GUI.  GUIs lie.
Use the CLI.

If a file system local or remote is "mounted", then it will show up with the 'df' command.  **df -Th** is very helpful.

To see the permissions/options used in a mount, use the 'mount' command.  No options.  That will show all mounts with all the options. 

Foreign file systems are still required to have permissions even if they don't support native Unix permissions.  A very common problem is that the permissions created during the mount of a foreign file system has the wrong permissions. It is not automatic.  NTFS and Samba/CIFS are foreign.

If you are mounting using NFS, then native file permissions are used.  The link I provided in my first reply is a minimum level of knowledge needed to work with those. This isn't optional.  Every file and every directory on any Unix system has permissions, owner, group, and perhaps xattrs and ACLs. 

If I assume you are using Samba/CIFS mounts with the NAS, then I'd do something like this:
```
$ df -Th 
Filesystem                        Type  Size  Used Avail Use% Mounted on
....
//172.22.22.14/K                  cifs   74G   18G   57G  24% /Data/K
```
/Data/K is where I have a Windows system that shares some storage. I removed all the other mounted locations to keep the output clean here.

To see the mount options for it:
```
$ mount |grep K
//172.22.22.14/K on /Data/K type cifs (rw,relatime,vers=2.1,cache=strict,username=thefu,uid=1000,forceuid,gid=1000,forcegid,addr=172.22.22.14,file_mode=0664,dir_mode=0775,soft,nounix,serverino,mapposix,rsize=1048576,wsize=1048576,bsize=1048576,echo_interval=60,actimeo=1)
```
See the uid, gid, file_mode, dir_mode and username parts?  Those are forcing specific Linux users with permissions with a Windows login (thefu) used.
The 'grep K' is just a filter so 10 other mounts aren't cluttering up the output.  'K' is just a letter in the mount that I guessed would be unique to that mount. grep is a pattern matching program, 'K' in my use above. grep isn't necessary at all.

If your Synology supports NFS, that would be my preference, since it is usually faster, and because it does support native Unix permissions. I like Unix permissions.  But many people don't (why run Unix then???). Alas, Windows systems don't have an NFS server built-in - or at least mine do not.

Can you do commands similar to mine above for your situation and post the output using code tags, please?
After that is successful, we can look at the actual files or symbolic links that aren't working and where those things point. It is possible to have a link that can be accessed, but it might point to a directory or file that cannot be accessed due to permissions or as Holger_Gehrke said above, isn't mounted.

Storage doesn't automatically get mounted in Linux, unless we tell the system to mount it, always.

---

### Post by paullangdon678 on 2021-03-08
Ok thanks or the assistance.
 I have run commands with the results below. I should add that I have changed the setting on my Synology Drive Client so that On-Demand-Synch is off. This means that I can now access the Toshiba Drive sdc1 fine now and open files. Not sure if there is cure for this but not too fussed as I am not short of disk space at the moment.
However I am not home and dry yet as I cannot set Synology Drive client to synchronise that drive does not appear. Nor can music apps see it (it is not offered as a location choice) other than Rythmbox which seems to have no problem.
Sorry I might have missed something - not sure what you meant by 'using code tags'. I have probably included too much but better that than too little.
Still working through Ubuntu unleashed...
```

**psas@LianLi:~$ sudo df -Th**
Filesystem     Type     Size  Used Avail Use% Mounted on
tmpfs          tmpfs    786M  4.0M  782M   1% /run
/dev/nvme0n1p5 ext4      48G   39G  6.3G  87% /
tmpfs          tmpfs    3.9G     0  3.9G   0% /dev/shm
tmpfs          tmpfs    5.0M  4.0K  5.0M   1% /run/lock
tmpfs          tmpfs    4.0M     0  4.0M   0% /sys/fs/cgroup
/dev/nvme0n1p1 vfat      96M   33M   64M  35% /boot/efi
tmpfs          tmpfs    786M  148K  786M   1% /run/user/1000
/dev/sdc1      fuseblk  932G  170G  762G  19% /media/psas/STORAGE Tosh 1TB

```

```
[B]
psas@LianLi:~$ mount |grep sdc1[/B]
/dev/sdc1 on /media/psas/STORAGE Tosh 1TB type fuseblk (rw,nosuid,nodev,relatime,user_id=0,group_id=0,default_permissions,allow_other,blksize=4096,uhelper=udisks2)

```

---

### Post by TheFu on 2021-03-08
Code Tags: [https://ubuntuforums.org/misc.php?do=bbcode#code](https://ubuntuforums.org/misc.php?do=bbcode#code)
Things that come from the terminal need to line up. Code Tags does that when posting here.

---

### Post by paullangdon678 on 2021-03-10
Great thanks, So done.
Puzzled though as the last line of output shows rw - I interpret that as sdc1 one should allow write and read. 
Folder permissions are rw on SDC1.

I cannot save files to this drive from another drive. I get this when I try to do so:
[http://gofile.me/5zaWR/Kh0pOPOrE](http://gofile.me/5zaWR/Kh0pOPOrE)
I can open on the drive, edit but cannot save files.

The Toshiba drive is more visible now and music files can be played but cannot be edited.

I can save to the location /homes for borisp. I assume what I am doing here is working directly on the NAS.

Finally my Synology drive is formatted btfrs. The Toshiba drive sdc1 is NTFS. I have used btfrs on the NAS as this is needed for services I am using on the NAS.
I cannot add images inline to this post as the paperclip is not working for me.
 Perhaps Linux is not for me :-)

---

### Post by TheFu on 2021-03-10
> **paullangdon678 said:**
> Great thanks, So done.
Puzzled though as the last line of output shows rw - I interpret that as sdc1 one should allow write and read. 
Folder permissions are rw on SDC1.
So - that isn't the entire story and df doesn't say anything about directory permissions. It only says stuff about mounts.  The mount is rw. That is an important difference.```

$ mount |grep sdc1
/dev/sdc1 on /media/psas/STORAGE Tosh 1TB type fuseblk (rw,nosuid,nodev,relatime,user_id=0,group_id=0,default_permissions,allow_other,blksize=4096,uhelper=udisks2)
```
This tells us:
[LIST]
[*]The label for this storage as spaces in is. That will be a hassle for the rest of the time. I'd fix that. No spaces in any labels, directories, filenames. Spaces just cause problems.
[*]Appears that udisks2 did the mount and that this file system is NOT a native Linux file system. That's bad. I'd guess it is NTFS.
[*]The owner and group are both root, which really isn't useful for most people.  
[/LIST]

First, I'd remove all the data on the disk (make a backup), then format it into ext4 as the file system. This is native to linux and solves many issues you have now. I don't care how you format the partition to ext4.  You can use mkfs or gparted. Doesn't matter.  At the same time, I'd set the label so it doesn't have any spaces or punctuation characters.  "Tosh_1tb" or something like that?

Second, I'd use the fstab to mount the storage. You can use the LABEL= option.
```
LABEL=Tosh_1tb     /media/Tosh_1tb    ext4    noatime,nofail    0   2
```
Spaces are the delimiter, so don't put any spaces where I haven't shown any.  1 or 20 spaces is fine. That doesn't matter.
That line added to the bottom of the /etc/fstab file will do it. Use **sudoedit  /etc/fstab** to edit the fstab (or any system config file). Other methods aren't as safe. Then run **sudo mount -a** and it should mount. At every reboot, it will be automatically mounted too.  If you don't plan to leave it connected all the time, say something now.  As that config line is now, it will complain loudly if the disk isn't connected.
**df -Th** will check what is and isn't mounted.

Third, we need to set the permissions and group correctly for your needs. NTFS doesn't support this, so it was always going to be a hassle with that file system.  Native Linux file systems allow fine-grained control and changing of the permissions for each file/directory object.  To start, make your userid the owner of everything.
```
sudo chown -R psas /media/Tosh_1tb
```
That will be the last time you need to use sudo.  You'll have full modification for everything on the partition.
If it were me, I'd lock down the permissions a little more - 
```
chmod -R 755 /media/Tosh_1tb
```
Then you can copy back the files that were removed before formatting.

I wouldn't use brtfs for a number of reasons.  But it is your disk. Feel free if you want btrfs rather than ext4.  I can't help with that.

```
psas@LianLi:~$ sudo df -Th
Filesystem     Type     Size  Used Avail Use% Mounted on
/dev/nvme0n1p5 ext4      48G   39G  6.3G  87% /
/dev/nvme0n1p1 vfat      96M   33M   64M  35% /boot/efi
/dev/sdc1      fuseblk  932G  170G  762G  19% /media/psas/STORAGE Tosh 1TB
```

No need for sudo in that command.  sudo abuse is a good way to break your system, though it didn't do any harm for that command.

---

### Post by paullangdon678 on 2021-03-11
Thanks,
The directory permissions for the Synology Drive location on the Toshiba Drive does have read and write permissions and I can edit a file there but it doe not save. Says there is a write error and file cannot be written.
You are right - the Toshiba drive is NTFS - I am sharing with Windows at the moment so will keep to that but if I get more confident about Ubuntu as a longer term thing I will change.
I have effected the other changes you have suggested - great thanks.
I have a few other issues with Ubuntu at the moment. When the PC is not used for a period of time or suspended I cannot login to Ubuntu but have to rerboot. I am also having some display issues.
I think I will call a halt here and spend a bit more time getting up to speed. In a sense I am ok in that I can ignore the Tosh Drive and work on the network one and all the saves are reflected onto the NAS and then back to Windows.
I will move from Windows when work allows and I have bottomed out Ubuntu a bit more or a lot more!

Thanks for all the help. The support here looks really good which is comforting.

---

### Post by TheFu on 2021-03-11
If you aren't physically moving the storage between Linux and Windows, then you don't need NTFS. If the storage is connected to Linux or a NAS, then the network protocol, usually CIFS for Windows clients, will handle the conversion that Windows wants.  And you are stuck with poor permission controls under the Linux/Unix OSes.

NTFS permissions on Linux can only be set by mount options.  That controls the users, groups, and permissions. Chown, chmod do not work on NTFS storage.

---

### Post by paullangdon678 on 2021-06-02
I have returned to this and simplified things. No longer dual booting with Windows.
I have renamed my 'storage' disk as Storage_Tosh and formatted as ext4.
I cannot copy files to it or create folders to or within it so I think I have a permissions issue. 
If the drive is NTFS I can use it fine.

It puzzles me that this does not just work - I would have thought I could format the drive and then be able to use it. Is there something fundamentally wrong here or is this what you would expect?

The (relevant results df -Th are below:
/dev/sda1                                        ext4   916G   72M  870G   1% /mnt/Storage_Tosh

Following your advice previously I have added a line to FStab as below> But I cannot work out how to save, having added it?
LABEL=Tosh_1tb     /media/Tosh_1tb    ext4    noatime,nofail    0   2

---

### Post by TheFu on 2021-06-02
Storage that is directly connected to a Linux system, using a native Linux file system like ext4, should be mounted, then use **chown **and **chmod** to make it accessible to the userids and groups of users you need.  By default, mounts are owned by root:root. This is expected and normal for all Unix-based systems.

You probably want to use a command like this on a single-user system:
```
sudo chown -R $USER  /media/Tosh_1tb
```
Then you can modify the file and directory permissions going forward without ever needing sudo again.  Owners of files and directories can chmod.
Why was sudo used for the chown command?  Because everything was owned by root.  Only root can chown - give away ownership.

My first post was about file permissions, btw.  That is exactly what is happening here.  Normally, I warn people that not learning them will lead to hours, day, weeks, months or years of frustration.  I see it has been since early Feb with this issue. Please just spend the concentrated 45 minutes needed to learn file permissions.  There's no way around it and no need to be frustrated by this stuff. It does all make sense and is quite elegant in how it all works. I promise.

---

### Post by paullangdon678 on 2021-06-02
Thanks. Looking at this has been delayed due to some work on my NAS and working towards breaking my Windows dependency.
I am setting aside some time this week to try to understand this better.
I have tried the 'chown' command and Ubuntu reports it cannot find the drive. 
I have formatted the drive as NTFS and it works fine. Once I have a better understanding I might try ext4 again.
Thanks for all your time and help.

---

### Post by TheFu on 2021-06-02
When you want to try again, please start a new thread and provide a link to this one if you think it won't confuse people.  Reviewing it, it seems you've been all over the place.

1 thread = 1 issue. That's the best way to get help.  Choose either NTFS or ext4. Don't mix those up in the questions.  If the drive is only connected to a Linux computer, use ext4. No reason to use NTFS ever, if it isn't DIRECTLY connected to Windows.  Over the network is not DIRECTLY connected.

Best of luck.

---

### Post by paullangdon678 on 2021-06-04
Yes that is fine I revise the thread moved into different territory. I accept there should be no reason to use NTFS in my situation. However,and I do not pretend to understand why. Ext4 does not work for me 'out of the box' and NTFS does.
I imagine I will be back on the forums when I get into this more. And hopefully it will be Ext4 based rather than NTFS :-)
Thanks for your help to date.

---

### Post by TheFu on 2021-06-04
The steps are easy, when you know them.  These steps apply to local, directly connected, storage:

[LIST=1]
[*]Connect the drive; sata, esata, usb, infiniband. Just needs to be directly connected - with a wire and not over networking.
[*]Use **gparted** to force-create a *GPT partition table* and 1+ partitions.
[*]Still in gparted,  *format* the partition as ext4 ; for Flash storage, may wan to choose *f2fs* as the file system.
[*]Still in gparted, *label* the partition, say "STUFF-1"  ; Tips: No spaces, no funny characters or punctuation, must be unique
[*]Still in gparted, click the "_Apply_" *check* icon to actually carry out the prior choices.
[*]Choose where to mount the storage and create an empty directory in that location.  /mnt/stuff-1 Tips: choose storage under /mnt/ or /media/ if you use snap packages.  However, any empty directory at any level can be used, except /.  I put data drives under /d/D1, /d/D2, /d/D3, /misc, /stuff and backups under /d/b-D1, /d/b-D2, /d/b-D3, for example. Snap programs cannot access any of those locations outside /mnt/ or /media/ and only if the constraints for the snap package supports the removable media option.
[*]Edit the /etc/fstab to mount the storage.  ```
sudoedit /etc/fstab
``` ; Tip: **sudoedit** is the safe way to edit system files. Any editor we prefer can be configured to be used and still be safe.
[*]Add this line: ```
LABEL=STUFF-1  /mnt/stuff-1  ext4  nofail,noatime,errors=remount-ro   0   2 
```  Tip: spacing (AND lack of spaces) is very important in this line.  The options area cannot have any spaces. Between each grouping, 1 or more spaces is fine. It must be a single line per mount. Also, add 1 blank line to the end of the file. That's a good tip for all Unix config files. Never have the last config line end the file, always have an <CRLF>, then <EOF> marker.
[*]Mount the storage: ```
sudo mount -a
```
[*]Verify the mount happened: ```
df -Th | egrep -v 'tmpfs|loop'
  or
df -Th | egrep stuff
```
[*]Change the owner of the mounted storage to your userid.  ```
sudo chown -R $USER: /mnt/stuff-1
```  That command recursively changes the owner to the current USERID and default GROUPID, probably you. For a single-user system, this is probably what you want.  On a multi-user system, maybe that storage needs to be shared?  Be very careful with chown.  If you do it on the OS files, you'll get a system that won't boot or a completely non-secure system. Reinstall is the only fix - or restore from backups.
[/LIST]

That's it.  Use the newly formatted, mounted, and storage under /mnt/stuff-1 .  Order of the commands matters for some parts, but not all.

You can change the permissions for any files or directories under /mnt/stuff-1 as you like.  For example, it might be nice to give your spouse a different directory only for that person.
```
mkdir /mnt/stuff-1/Joe   /mnt/stuff-1/Daisey    /mnt/stuff-1/Shared
chown daisey /mnt/stuff-1/Daisey
```
Now she can use /mnt/stuff-1/Daisey and have complete control over permissions for files and subdirectories there.

Just to be clear, the label and mount directory do not need to have similar names at all.  I'm just following the KISS Principle. [https://en.wikipedia.org/wiki/KISS_principle](https://en.wikipedia.org/wiki/KISS_principle)  to limit confusion.  Also, I think that using either /media/ or /mnt/ for storage that will always be available is incorrect, but most people want to use snaps and the snap team decided to hard-code those locations into their constraints.  For the official "where stuff belongs", see: [https://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard](https://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard) which says: 
>     /media 	Mount points for removable media such as CD-ROMs (appeared in FHS-2.3 in 2004).
    /mnt	Temporarily mounted filesystems. 


If you want a shared area for both users to have write/read access, then put those userids into a Unix group. /mnt/stuff-1/Shared would be the place. Search these forums for "working together" and my account here for steps.

Actually, I think I'll save the steps above. No reason for this stuff to be hard or too confusing.
If you don't want to use gparted, there are other tools for partitioning (parted/fdisk), setting a label (e2label), and creating a file system (mkfs). Shouldn't matter which is used. Using a label makes things easier for humans.  UUIDs can be used and there are a number of other methods available which are good for systems with 20+ disks to prevent admins from becoming confused about storage connected to each controller card. End-users wouldn't use these other methods.

---

