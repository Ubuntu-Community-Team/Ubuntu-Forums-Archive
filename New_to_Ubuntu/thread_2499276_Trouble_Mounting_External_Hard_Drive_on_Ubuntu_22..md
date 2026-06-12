---
title: "Trouble Mounting External Hard Drive on Ubuntu 22.04"
date: 2024-07-21
forum: New to Ubuntu
---

### Post by modismos on 2024-07-21
Hi everyone,


I'm new to Ubuntu and recently installed version 22.04 on my laptop. I'm having trouble mounting my external hard drive. When I connect it, the drive shows up in the file manager, but when I try to open it, I get an error message saying, "Unable to access location - Not authorized to perform operation."


I've tried searching for solutions online but haven't had much luck. I've already checked the permissions and tried using the mount command in the terminal, but I keep running into permission issues.
Has anyone else faced this problem?

Any help would be greatly appreciated

Thanks and Regards,
Elena [Idioms]("https://www.theidioms.com")

---

### Post by Rubi1200 on 2024-07-21
Welcome to the forums :-)

Open a terminal with Ctrl+Alt+T and then run this command:
```
lsblk -f
```

Copy the output and when replying click on Go Advanced >> paste the output >> highlight the text and then click on the # icon on the toolbar.

This will wrap the output with code tags making it much easier to read and analyze.

---

### Post by yancek on 2024-07-21
> I've already checked the permissions and tried using the mount command in the terminal, 

So members don't waste their time suggesting you try specific things, how about if you indicated what those permissions are as well as the owner:group?  Also, what filesystem is on the drive partition(s)?  What mount command did you use and what was the result?

---

### Post by modismos on 2024-07-22
> **yancek said:**
> So members don't waste their time suggesting you try specific things, how about if you indicated what those permissions are as well as the owner:group?  Also, what filesystem is on the drive partition(s)?  What mount command did you use and what was the result?

Thanks for your response!
Here's the information you asked for:

[B]Permissions and Owner:Group:

[/B]I checked the permissions using ls -l /media/mydrive and got the following:


```
drwxr-xr-x 2 root root 4096 Jul 21 15:23 mydrive

```

[B]Filesystem:
[/B]The filesystem on the drive partition is NTFS. I confirmed this using sudo fdisk -l, which shows:


```
Device     Boot Start       End   Sectors   Size Id Type
/dev/sdb1        2048 1953525167 1953523120 931.5G  7 HPFS/NTFS/exFAT

```
[B]Mount Command and Result:
[/B]
```
sudo mount -t ntfs-3g /dev/sdb1 /media/mydrive

```

[B]The result was an error message:
[/B]

```
ntfs-3g-mount: failed to access '/dev/sdb1': Permission denied

```

Any advice on what to try next would be greatly appreciated!

---

### Post by modismos on 2024-07-22
> **Rubi1200 said:**
> Welcome to the forums :-)

Please accept my thanks for your assistance and warm welcome. I will check it out and let you know soon.

Elena

---

### Post by yancek on 2024-07-22
Standard Linux permissions (rwx) are not used on ntfs filesystem.  You need to have an entry in the /etc/fstab file with the parameters you want which you can search here at the forums or do an online search to look for permissions to read/write to ntfs from Ubuntu/Linux.  I don't use windows so don't have any entry as an example.  Why do you have an ntfs filesystem?  Do you also have some windows installed?  Do you share data on this drive with other windows users?

Have you successfully accessed this drive before?  Have you always had this problem with the drive?  Did you use this drive on a windows machine?   If you have not used the drive yet and there is not data on it and you don't use it with windows, reformat it with an ext4 or other Linux filesystem.

---

### Post by TheFu on 2024-07-22
NTFS doesn't support the standard ways that Linux manages users, groups, permissions.  It is a foreign file system and should only be used if you have to physically connect the storage to a non-Linux OS.   For Linux use only, it would be best to use a native linux file system, perhaps ext4 or xfs.  Of course, there's no direct conversion tool, so backup any data you don't want to lose, then use something like **gparted** to format the partition your selected file system.  If you also add a LABEL to the file system, you'll be able to mount it using that LABEL, instead of the ugly UUID.  The LABEL works for mounting even if you keep NTFS.

To mount the storage, you'll want to use **sudoedit** to modify the /etc/fstab file, adding a new line. Something like 
```
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
LABEL=Recordings   /Recordings    ntfs nodev,windows_names,nosuid,noatime,async,big_writes,uid=1000,gid=1000,fmask=0002,dmask=0002  0   0
```

The uid/gid numbers will be specific to your user on the system.  Typically, 1000 is the userid created during installation, so it is the first userid.  Same for the gid.  This 2 settings control the owner and group for all the directories and files on the storage.  The fmask and dmask settings are important too. Those control the POSIX permissions.

Of course, you'll need to replace "Recordings" in the 2 places to map to the LABEL you set and where you want it mounted.  I didn't add options for storage that isn't always connected. You might want to do that.  With USB connected storage, I wouldn't use the fstab method for mounting, but the way I do it is about 2x harder than just adding 1 line to the fstab file.

---

### Post by ActionParsnip on 2024-07-22
I also suggest you connect it to a Windows system and run a full chkdsk to make sure the file system is complete and consistent. Once this is done, use the safe remove feature in the OS and only unplug the USB plug when prompted. You'll find this helps. The NTFS access you enjoy is a best effort attempt and only Microsoft knows how NTFS really works.

---

### Post by TheFu on 2024-07-22
```
$ sudo mount -t ntfs-3g /dev/sdb1 /media/mydrive
ntfs-3g-mount: failed to access '/dev/sdb1': Permission denied
```

Does  /media/mydrive exist?  It must BEFORE a mount is allowed. It should be an empty directory.  If it does, then perhaps MS-Windows left the NTFS file system open.  That's a "feature" of MS-Windows since v8.  MSFT decided that fully opening and closing file systems, slowed down access to storage, so they made the default NOT to do it.  If the flag on the file system has it marked as "open", then Linux will refuse to mount it.

I should have more clearly said that trying to access/mount temporary storage devices using the device name, /dev/sdb1, which is temporary and prone to changes isn't a good idea.  Use the UUID or LABEL instead.  A LABEL is easier for a human than using UUIDs which are random sequences trying to be unique.

---

