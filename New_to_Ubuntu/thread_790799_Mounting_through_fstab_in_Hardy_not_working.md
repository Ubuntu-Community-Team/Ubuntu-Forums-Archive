---
title: "Mounting through fstab in Hardy not working"
date: 2008-05-11
forum: New to Ubuntu
---

### Post by Stegga on 2008-05-11
Hi there,

I have just upgraded to Hardy, and I have a samba share on my server that I connect to.
The server is called filestore and there is a share called sms on it and I have all required rights to access it.

I have a line in my /etc/fstab which looks like this:
//filestore/sms /mnt/sms smbfs user,credentials=/root/.credentials,fmask=777,dmask=777,auto 0 0

This worked fine in 7.10, but now after the upgrade it doesn't.
I have a file called .credentials in the /root directory which has the username and password, and as I said it worked fine until Thrusday when I did the upgrade.

The error I get is:
WARNING: 'fmask' not expressed in octal.
WARNING: CIFS mount option 'fmask' is deprecated. Use 'file_mode' instead.
WARNING: 'dmask' not expressed in octal.
WARNING: CIFS mount option 'dmask' is deprecated. Use 'dir_mode' instead.
mount error: could not find target server. TCP name filestore/sms not found
No ip address specified and hostname not found

PLEASE can someone help me with sorting this out!
I can't get to the server.

Cheers,
Andrew

---

### Post by cnkbrown on 2008-05-13
I had to replace fmask=775 with file_mode=0775, and similar with dmask.  However, my shares still do not mount.  I get;

mount error 13 = Permission denied
Refer to the mount.cifs(8) manual page (e.g.man mount.cifs)

---

### Post by Stegga on 2008-05-15
I received this reply from dbott67:
1. Change from 'smbfs' to 'cifs'
2. Change fmask=777 to file_mode=0777
3. Change dmask=777 to dir_mode=0777
 
Original fstab entry using 'smbfs':
 
//filestore/sms /mnt/sms  smbfs user,credentials=/root/.credentials,fmask=777,dmask=777,auto 0 0
 
Updated fstab entry using 'cifs' (changes are in red; also note that I removed the 'user,' part above):
 
//filestore/sms     /mnt/sms        cifs   credentials=/root/.credentials,dir_mode=0777,file_mode=0777 0 0
 
I also read in a thread about the use of the 'noperm' option:
 
[http://ubuntuforums.org/showthread.php?t=773483](http://ubuntuforums.org/showthread.php?t=773483)
 
Good luck.
 
-Dave

---

### Post by jflarm on 2008-05-15
Try changin the masks to 077. With those masks you are not giving permition for anything or to anyone. The mask says what you can NOT do.

---

### Post by Stegga on 2008-05-15
If I type: sudo mount.cifs //192.168.10.5/sms     /mnt/sms     cifs     credentials=/root/.credentials,dir_mode=0777,file_mode=0777 0 0 then I get the following:
password:
I type in the password and I get the following error:
mount error 13 = Permission denied
Refer to the mount.cifs(8) manual page (e.g.man mount.cifs)

Sorry to be so disjointed, but I'm trouble shooting as I write this.
: mount
gives me the following:
/dev/sda1 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
**//192.168.10.5/sms on /mnt/sms type cifs (rw,mand)**

This means that the mount is mounting:
I now go to /mnt
and I see the directories that I have got for the mounts, and the sms one has an orange circle with a cross in the top right corner (permission problems, I think) so this means that the mount command is running, but the password and username are wrong!

If I 'Connect to Server', then this username and password work fine.

If I type:
:sudo mount.cifs //192.168.10.5/sms     /mnt/sms     cifs     user=andrew,pass=mypassword,dir_mode=0777,file_mode=0777 0 0

I get the same above error, (mount error 13) so it seems as if mount.cifs isn't getting in with the password that actually is correct?
ANY IDEAS?!

---

### Post by Stegga on 2008-05-15
I changed the masks, but nothing else happened. I'm getting no errors, but nothing is mounting - it's like my honeymoon coming back to haunt me!

---

### Post by wjhobbs on 2008-05-15
Stegga,

Have a look at this thread to see if any of it helps.

[http://ubuntuforums.org/showthread.php?t=792508](http://ubuntuforums.org/showthread.php?t=792508)

---

### Post by Stegga on 2008-05-16
SOLVED - ish

My line in /etc/fstab is the following and it works fine.

//192.168.10.5/sms /mnt/sms cifs uid=andrew,credentials=/root/.credentials 0 0

The only issue that is not resolved, is the desktop shortcuts that used to be created with the smbfs line are no longer there, so I need to probably create a 'bookmark' the the /mnt/* directories to get to them that way.

I'm off to watch a weekend of Super14 Rugby - go Stormers!

Andrew

---

