---
title: "Help with group level permissions for a NTFS Partition on Ubuntu Release 18.04.1 LTS"
date: 2018-11-15
forum: New to Ubuntu
---

### Post by 52callaway on 2018-11-15
Hello, I have been trying to set group level permissions for a folder on a NTFS partition using the command getfacl and setfacl:

**To view the permissions**
john@ubuntu1030:/$ sudo getfacl media/john/External/1030Share
# file: media/john/External/1030Share
# owner: john
# group: john
user::rwx
group::rwx
other::rwx

**To Set the permissions**
john@ubuntu1030:/$ sudo setfacl -m g:sambashare:rwx media/john/External/1030Share

**To check to see if it worked**
john@ubuntu1030:/$ sudo getfacl media/john/External/1030Share
# file: media/john/External/1030Share
# owner: john
# group: john
user::rwx
group::rwx
other::rwx

Would you have to restart the samba service to see a change? Did that, no change!

Basically nothing seems to work!  Any help would be appreciated!

---

### Post by TheFu on 2018-11-15
[https://askubuntu.com/questions/301494/how-to-change-ntfs-acls-on-linux](https://askubuntu.com/questions/301494/how-to-change-ntfs-acls-on-linux) says that NTFS doesn't support ACLs when using the Linux FUSE driver.  It is old. Need to check the newer manpage to see if that is still true.

I don't have 18.04, but the 16.04 manpages are useful.  Check the manpages on your system for the details.

Appears that ACL support has to be enabled at mount time according to the mount.ntfs manpage:```

       acl    Enable  setting  Posix  ACLs  on  created files and use them for
              access control.  This  option  is  only  available  on  specific
              builds. It is set by default when a user mapping file is present
              and the permissions mount option is not set.
```
So, do you have a usermapping file and are the mount options NOT including the permissions option?

How to enable this for Samba is a different question.  I've never attempted to share NTFS formatted disks over Samba. NTFS mounts are slower than using Linux file systems which have kernel mounts and support full POSIX permissions. Just something to consider.

The manpage for smb.conf has a number of sections mentioning ACL configuration. Some are deprecated, but not all.
```

       acl group control (S)

           In a POSIX filesystem, only the owner of a file or directory and
           the superuser can modify the permissions and ACLs on a file. If
           this parameter is set, then Samba overrides this restriction, and
           also allows the primary group owner of a file or directory to
           modify the permissions and ACLs on that file.
....
``` Lots more in that section.

For Samba help, please post the output from **testparm** run on the Samba server.

Your example doesn't require the use of ACLs. Normal POSIX permissions should work fine, er, if a Linux file system was used. Without a user mapping file on the NTFS disk, the owner, group, and permissions have to be set at mount time if ACLs don't work.

Found this page on the Samba.org site [https://wiki.samba.org/index.php/Setting_up_a_Share_Using_Windows_ACLs](https://wiki.samba.org/index.php/Setting_up_a_Share_Using_Windows_ACLs)
[https://wiki.samba.org/index.php/File_System_Support](https://wiki.samba.org/index.php/File_System_Support) says that only EXT3, EXT4, and XFS support the required extensions to support ACLs in Samba.  There is a section *File systems without xattr support* that provides a workaround, but it isn't recommended.

---

