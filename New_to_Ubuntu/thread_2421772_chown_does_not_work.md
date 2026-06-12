---
title: "chown does not work"
date: 2019-06-26
forum: New to Ubuntu
---

### Post by mwoosley on 2019-06-26
Hello everyone... I am finding it hard to believe I have to post this question, but for the life of me, I cannot get the 'chown' command to work for me.  

I've been working towards a backup strategy using 'crontab' / 'rsync' and apparently, my destination for backups is NOT owned by me.

With that being said, I typed in one of several commands, ie; sudo chown -R /mnt/backups/dir1/ and I get 'Operation not permitted'.
If I type in sudo chown -R me:me /mnt/backups/dir1/ I still get 'Operation not permitted'.

Using several websites for reference, I realize there are several ways to transfer ownership, but none seem to work for me.  I know it's got to be something super silly, but I cannot figure it out.

I even logged in as root and got the same responses.

HELP!!

---

### Post by CatKiller on 2019-06-26
Permissions for mounted partitions are set in /etc/fstab and with the permissions of the mount point. There's no guarantee that *any* user is able to write there, depending on how you've mounted it.

---

### Post by TheFu on 2019-06-27
What file system is on the target disk?  NTFS?  FAT32?  NFS?  Without some setup chown won't work on those and other metadata about each file is being lost.

---

### Post by mwoosley on 2019-06-27
TheFu, I originally had defaults set as my option, but have since changed the options to defakults,umask=000,user.  I know the umask option is not very secure, but I'm only setting it in this manner to help me at least get SOME permission.

The file system is VFAT by the way

---

### Post by TheFu on 2019-06-27
Way to bury the lead.  vfat doesn't support any file permissions.  Attempting to use chown is a lost cause on that file system. It will NEVER, EVER, EVER, EVER work. There is no way to make it work. 

At mount time, you can set 1 userid as the owner and 1 group as the group for all files.  In a mount command, that would look like:
```
sudo mount -t vfat -o uid=1000,gid=1000 /dev/path/to/partition /mnt/path/to/mount-point-directory
```
Does that work, after you change the  uid/gid and both paths to what you need?  

From the manpage for exfat mounts:
```
FILE SYSTEM OPTIONS
       umask=value
              Set  the  umask  (the  bitmask  of  the permissions that are not
              present, in octal).  **The default is 0**.

       dmask=value
              Set the umask for directories only.

       fmask=value
              Set the umask for files only.

       uid=n  Set the owner for all files and directories.  The default is the
              owner of the current process.

       gid=n  Set the group for all files and directories.  The default is the
              group of the current process.

```
I don't have any vfat file systems here anymore, so can't check that manpage, but the options are probably the same from exfat. Best to check your local manpage for mount.vfat.

BTW, trying to backup files to a vfat file system will lose all the metadata about those files.  That might be fine if only 1 userid's files are involved and they are purely data.  It wouldn't be sufficient to backup any of my HOME directories because the file permissions needed are explicit for many directories due to security needs.

For a system backup, it just won't work.  Use a Unix file system for backups and use a better backup tool that does the data and metadata about all the files.

For a tiny amount of files, you could create a tar.gz file with all the files. That way the directory structure, owner, group, and permissions will be retained.  I wouldn't use tgz files for anything over about 300MB of files.

---

### Post by mwoosley on 2019-06-28
TheFu, thanks again for all your pointers.  BTW, the lead is hard to remove once embedded, Lol (but I'm working on it).  As I  told you in my crontab thread, I'm gonna change over the file system to ext4 to lessen the issues I'm having  trying to manipulate files.

My only minor issue (maybe) is how and if I can, convert my boot/efi partition to a Linux style.

Thank you and I appreciate very much all your help.

Best regards.

---

### Post by CatKiller on 2019-06-28
> **mwoosley said:**
> My only minor issue (maybe) is how and if I can, convert my boot/efi partition to a Linux style.

EFI needs to be FAT. Microsoft's dominance meant it became part of the SD standard, which meant that it became part of the EFI standard, or something like that.

It's not like you can put files in your EFI as a normal user anyway. Whatever you do, don't try to make that anything other than FAT.

---

### Post by TheFu on 2019-06-28
Picking a good file system is much easier these days, but still needs some thought.

If flash storage is being used, then it is best to use a flash-aware file system. Writes are the enemy. A journaled file system will write much more and wear out the flash chips.  There are flash memory file systems for Linux that support POSIX permissions and ACLs. I've never used any, but I have destroyed a few USB flash storage devices by writing to them almost daily for a year. These were name brand flash devices with good reviews.

I use Ext4 for both quality SSD and spinning disk storage. I've also had cheap SSDs fail after less than 2 yrs of use.  Just sayin'.  If using SSD for this, monitor the TBW warranty and actual TBW numbers. Use a long SMART test weekly to help monitor those values.

---

