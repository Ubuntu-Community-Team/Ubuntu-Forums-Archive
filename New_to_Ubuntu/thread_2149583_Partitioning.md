---
title: "Partitioning"
date: 2013-05-29
forum: New to Ubuntu
---

### Post by tknudsen on 2013-05-29
Hi all

I have a case where I do not fully understand how to go about things in order to get the things I want done.

Case!

1. I have two harddrives 
- 200GB
- 3000GB

2. I want lubuntu or ubuntu running as primary OS on the 200GB disk

3. I want the 3000GB to be used for only filestorage / backup

So, how do I partition this?  

PS..
The 3000GB needs to be split into two disk since my bios does not support large disk format


Please help :)

---

### Post by ajgreeny on 2013-05-29
When installing Lubuntu choose "Something Else at the partitioning or disk preparation stage and you can then make the partitions "on the fly".

I suggest you have:-
20 - 25GB partition, ext4, mountpoint / (root) on 200GB disk.
2 - 4GB partition, swap, no mountpoint needed for this, on 200GB disk, See below for swap size discussion. [COLOR=#ff0000]**[/COLOR]
Remainder of disk, ext4, mountpoint /home.

On the large 3000GB disk you can make your data/storage partitions, ext4, but do not at this stage give them mountpoints; that will come later with a manual edit of /etc/fstab.  If you need to share these partitions with a windows OS at any time in the future, use ntfs for these, though ext4 is better if you are entirely Linux.

[COLOR=#ff0000]**[/COLOR] Swap size is not fixed, but is worth having even if you have lots of ram; if you want to hibernate you will need as much swap as you have ram, but if hibernation is not something you want, I suggest you stick at the 4GB, however much ram you have. If you have lots of ram and do not want to hibernate you could get away with no ram at all, but I like to play safe with a min of 2 - 4GB.

If that makes sense to you come back once installed and we can tell you about mounting the storage partitions.

---

### Post by tknudsen on 2013-05-29
ok, will try and reinstall now following your steps..

---

### Post by tknudsen on 2013-05-29
Ok, so now my setup is partitioned like this

200GB
    - /dev/sda1 ext4 /  (root) 26498 MB
    - /dev/sda5 swap              4092 MB
    - /dev/sda6 ext4  /home  173334 MB

3000GB
    -/dev/sdb1 ext4           3000591 MB


lubuntu 12.10 is installed now at sda 200GB
apt-get update is done
apt-get dist-upgrade is done


So here is my intentions

1. Want to store files and share sdb1 with a windows network
2. Want to use XBMC so I can stream videos to my Samsung 3D television

---

### Post by ajgreeny on 2013-05-29
You said that you could not use a large partition and that sdb, the 3TB disk needed to be split into two partitions, but I see you have not done that yet.

Is that partition seen by ```
sudo fdisk -l
``` command, or is it invisible to the system?

As to using XBMC, I can't help you, but I think you can share an ext4 partition, or folders on it, over a network using samba, though that is something I have no experience of, not having any windows OS in the house.

---

### Post by tknudsen on 2013-05-29
Disk sdb1 3000GB shows up, but with a GPT partition table which is not supported by fdisk. It says to use gparted.
All information on the disk is shown..

---

### Post by tknudsen on 2013-05-29
So how did I mount it?

---

### Post by sandyd on 2013-05-29
Adding the entry to fstab
```

sudo nano /etc/fstab
sudo mkdir /media/storage

```

Add (on a blank line at the end)
```

/dev/sdb1 /etc/storage         ext4    defaults        0       1
```

The drive will be mounted at /etc/storage.

---

### Post by tknudsen on 2013-05-29
Thanks a buch

But why did you mkdir /media/storage and then mount /etc/storage folder on the device/sdb1?
Seems to me the logical would be to create a folder and mount that as well?

And for every folder I create I need to list it in fstab right?

---

### Post by PavelMan on 2013-05-29
On your first drive, sda, where the root partition is mounted, you create a folder, which is going to represent your whole partition sdb1. From this point on, whatever folders you create in that folder (/media/storage in the above example) - those will actually end up being created on your sdb1 partition. But you do not see that partition "directly" until you "mount" it somewhere. In the above example it was mounted as /media/storage.

So, no, you do not need to do anything for any sub-folders you create on sdb1, as those will be visible as folders inside /media/storage.

Oh, and creating /media/storage, but then later mounting /dev/sdb1 as /etc/storage was a typo, I guess... it should have been /media/storage (or at least the same thing)  in both cases.

---

### Post by tknudsen on 2013-05-29
Ok so now I have edited the fstab file to be /dev/stb1 /media/storage

/media/storage is also created to sda1 

Samba is installed and /etc/smb.conf is written to include /media/storage   (or should it be /dev/sdb1 /media/storage)
samba server is restarted 

but nothing is showing up in "network" on my windows pc

---

### Post by PavelMan on 2013-05-29
Assuming you have done prev. steps correctly, add to the end of your /etc/samba/smb.conf (or wherever it is, it already exists, just edit it)

[BackupMedia] backup location
path=/media/storage
public=yes
writable=yes
create mask=0777
directory mask=0777

Then restart samba with something like 

sudo service smbd restart

---

### Post by tknudsen on 2013-05-29
Thanks, will try

---

### Post by tknudsen on 2013-05-29
Sorry to say, but nothing is showing up in Windows

etc/fstab

> 

# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda1 during installation
UUID=b72f58ba-2fe4-4134-9b93-e38ca77ad4a6 /               ext4    errors=remoun$
# /home was on /dev/sda6 during installation
UUID=99330dd3-cd15-4b50-97b3-d9b2462dc088 /home           ext4    defaults     $
# swap was on /dev/sda5 during installation
UUID=3bf251a0-e902-42f2-a04e-41f435aaac3d none            swap    sw           $
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
/dev/sdb1       /media/storage                            ext4    defaults     $




/etc/samba/smb.conf

> 
[global]
netbios name = Samba24
server string = Samba file and print server
workgroup = Workgroup
security = user
hosts allow = 127. 192.168.1.
interfaces = 127.0.0.1/8 192.168.1.1/24
bind interfaces only = yes
remote announce = 192.168.1.255
remote browse sync = 192.168.1.255
printcap name = cups
load printers = yes
cups options = raw
printing = cups
guest account = smbguest
log file = /var/log/samba/samba.log
max log size = 1000
null passwords = no
username level = 6
password level = 6
encrypt passwords = yes
unix password sync = yes
socket options = TCP_NODELAY SO_RCVBUF=8192 SO_SNDBUF=8192
local master = no
domain master = no
preferred master = no
domain logons = no
os level = 33
logon drive = m:
logon home = \\%L\homes\%u
logon path = \\%L\profiles\%u
logon script = %G.bat
time server = no
name resolve order = wins lmhosts bcast
wins support = no
wins proxy = no
dns proxy = no
preserve case = yes
short preserve case = yes
client use spnego = no
client signing = no
client schannel = no
server signing = no
server schannel = no
nt pipe support = yes
nt status support = yes
allow trusted domains = no
obey pam restrictions = yes
enable spoolss = yes
client plaintext auth = no
disable netbios = no
follow symlinks = no
update encrypted = yes
pam password change = no
passwd chat timeout = 120
hostname lookups = no
username map = /etc/samba/smbusers
passdb backend = tdbsam
passwd program = /usr/bin/passwd '%u'
passwd chat = *New*password* %n\n *ReType*new*password* %n\n *passwd*changed*\n
add user script = /usr/sbin/useradd -d /dev/null -c 'Samba User Account' -s /dev/null '%u'
add user to group script = /usr/sbin/useradd -d /dev/null -c 'Samba User Account' -s /dev/null -g '%g' '%u'
add group script = /usr/sbin/groupadd '%g'
delete user script = /usr/sbin/userdel '%u'
delete user from group script = /usr/sbin/userdel '%u' '%g'
delete group script = /usr/sbin/groupdel '%g'
add machine script = /usr/sbin/useradd -d /dev/null -g sambamachines -c 'Samba Machine Account' -s /dev/null -M '%u'
machine password timeout = 120
idmap uid = 16777216-33554431
idmap gid = 16777216-33554431
template shell = /dev/null
winbind use default domain = yes
winbind separator = @
winbind cache time = 360
winbind trusted domains only = yes
winbind nested groups = no
winbind nss info = no
winbind refresh tickets = no
winbind offline logon = no

[homes]
comment = Home Directories
path = /home
valid users = %U
read only = no
available = yes
browseable = yes
writable = yes
guest ok = no
public = no
printable = no
locking = no
strict locking = no

[netlogon]
comment = Network Logon Service
path = /var/lib/samba/netlogon
read only = no
available = yes
browseable = yes
writable = no
guest ok = no
public = no
printable = no
locking = no
strict locking = no

[profiles]
comment = User Profiles
path = /var/lib/samba/profiles
read only = no
available = yes
browseable = yes
writable = yes
guest ok = no
public = no
printable = no
create mode = 0600
directory mask = 0700
locking = no
strict locking = no

[printers]
comment = All Printers
path = /var/spool/samba
browseable = yes
writable = no
guest ok = no
public = no
printable = yes
locking = no
strict locking = no

[pdf-documents]
path = /var/lib/samba/pdf-documents
comment = Converted PDF Documents
admin users = %U
available = yes
browseable = yes
writeable = yes
guest ok = yes
locking = no
strict locking = no

[pdf-printer]
path = /tmp
comment = PDF Printer Service
printable = yes
guest ok = yes
use client driver = yes
printing = bsd
print command = /usr/bin/gadmin-samba-pdf %s %u
lpq command =
lprm command =

[Storage]
path = /media/storage
comment = Backup Server
read only = no
available = yes
browseable = yes
writable = yes
guest ok = no
public = yes
printable = yes
locking = no
strict locking = no



---

### Post by tknudsen on 2013-05-30
Anyone?

---

### Post by PavelMan on 2013-05-31
remove the "printable = yes" line, it probably thinks this is a printer...
And, ofcourse, make sure /media/storage exists. put some file in there. then browse from a windows machine to \\IP\storage 
I just tried, it works for me. Do not for get to restart the smbd after modifying the /etc/samba/smb.conf

---

