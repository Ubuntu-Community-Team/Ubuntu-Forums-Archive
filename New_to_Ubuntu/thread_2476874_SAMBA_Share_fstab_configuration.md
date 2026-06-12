---
title: "SAMBA Share fstab configuration"
date: 2022-07-10
forum: New to Ubuntu
---

### Post by todolinuxvidz1 on 2022-07-10
Hello all,
I suspect this is an easy solution.
I am sharing folder locations over the network to Windows based systems.
The folders I share from my root drive work fine.
However all my additionally mounted drives can be detected and added but seeming not read from.
I suspect it has something to do with how they are mounted

Essentially UUID=5ED2-7C80 is able to share over the network just fine, but the others do not.   Any thoughts what I need to change?

> # /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/nvme0n1p2 during installation
UUID=19cc6a19-6d93-4c25-8b28-649f28d86704 /               ext4    errors=remount-ro 0       1
# /boot/efi was on /dev/nvme0n1p1 during installation
UUID=5ED2-7C80  /boot/efi       vfat    umask=0077      0       1
/swapfile                                 none            swap    sw              0       0
UUID=809E09029E08F288 /media/soloman/Core   ntfs       nodev,permissions,windows_names,nosuid,noatime,async,big_writes,timeout=2,uid=1000,gid=1000,fmask=0002,dmask=0002    0   0

UUID=4C50E4AA50E49C48 /media/soloman/Box   ntfs      nodev,permissions,window_names,nosuid,noatime,async,big_writes,timeout=2,uid=1000,gid=1000,fmask=0002,dmask=0002    0    0 


---

### Post by TheFu on 2022-07-10
Spaces aren't allowed in the options.  Appears you have at least 2 in each line which are not allowed.  

Also, if the storage will never be physically connected to a Windows system, it is better to reformat using a native linux file system for a multitude of reasons.

---

### Post by Morbius1 on 2022-07-11
[1] You mention samba but you didn't disclose how you set things up. Posting the output of the following commands would tell us that:
```
testparm -s
```
```
net usershare info --long
```
[2] Is the **[COLOR="#B22222"]soloman[/COLOR]** in /media/soloman/Core a user name?

If it is the only user that will get to the Core and Box subfolders is soloman regardless of the permissions on either folder.

Without knowing how these shares are configured try the following:

Right under the [COLOR="#0000CD"]workgroup = WORKGROUP[/COLOR] line in /etc/samba/smb.conf add the following:
```
force user = solomon
```
Then restart smbd:
```
sudo service smbd restart
```

---

### Post by todolinuxvidz1 on 2022-07-11
> **Morbius1 said:**
> [1] You mention samba but you didn't disclose how you set things up. Posting the output of the following commands would tell us that:
```
testparm -s
```
```
net usershare info --long
```



```
Load smb config files from /etc/samba/smb.conf
Loaded services file OK.
Weak crypto is allowed
Server role: ROLE_STANDALONE

# Global parameters
[global]
    log file = /var/log/samba/log.%m
    logging = file
    map to guest = Bad User
    max log size = 1000
    obey pam restrictions = Yes
    pam password change = Yes
    panic action = /usr/share/samba/panic-action %d
    passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
    passwd program = /usr/bin/passwd %u
    server role = standalone server
    server string = %h server (Samba, Ubuntu)
    unix password sync = Yes
    usershare allow guests = Yes
    idmap config * : backend = tdb


[printers]
    browseable = No
    comment = All Printers
    create mask = 0700
    path = /var/spool/samba
    printable = Yes


[print$]
    comment = Printer Drivers
    path = /var/lib/samba/printers


~$ net usershare info --long
[Temp]
path=/home/soloman/Desktop/Temp
comment=
usershare_acl=Everyone:R,Unix User\soloman:F,
guest_ok=y

[Shows]
path=/media/soloman/Box/Shows
comment=
usershare_acl=Everyone:R,Unix User\soloman:F,
guest_ok=y



```

> **Morbius1 said:**
> 
[2] Is the soloman in /media/soloman/Core a user name?

If it is the only user that will get to the Core and Box subfolders is soloman regardless of the permissions on either folder.

Without knowing how these shares are configured try the following:

Right under the workgroup = WORKGROUP line in /etc/samba/smb.conf add the following:
```
force user = solomon
```
Then restart smbd:
```
sudo service smbd restart
```

When I add the line force user = soloman that appears to make no change.
I mispoke earlier what I meant to say is that the drive UUID=19cc6a19-6d93-4c25-8b28-649f28d86704 appears to be able to share folders and files over the network to Windows based systems without any issues.  But the other drives cannot.   UUID=809E09029E08F288  & UUID=4C50E4AA50E49C48

---

### Post by Morbius1 on 2022-07-11
>  UUID=4C50E4AA50E49C48 /media/soloman/Box ntfs nodev,permissions,window_names,nosuid,noatime,asyn c,big_writes,timeout=2,uid=1000,gid=1000,fmask=000 2,dmask=0002 0 0 

The only user that can get to the "Box" folder is soloman. This is true locally and from the Windows machine.

**force user = soloman** under **workgroup = WORKGROUP**  followed by a **sudo service smbd restart** is the easiest answer here.

You say you added it to smb.conf but it's not in the output of **testparm -s**.

Nothing more I can do.

---

### Post by todolinuxvidz1 on 2022-07-12
> **Morbius1 said:**
> The only user that can get to the "Box" folder is soloman. This is true locally and from the Windows machine.

**force user = soloman** under **workgroup = WORKGROUP**  followed by a **sudo service smbd restart** is the easiest answer here.

You say you added it to smb.conf but it's not in the output of **testparm -s**.

Nothing more I can do.

The testparm -s I ran was before adding the force user information, and when I did that originally I mispelt the name as solomon ....opps.

Issue resolved, thanks so much for the assistance.

---

