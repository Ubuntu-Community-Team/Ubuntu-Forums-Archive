---
title: "Allow a folder share over Samba ?"
date: 2013-02-03
forum: New to Ubuntu
---

### Post by honeybear on 2013-02-03
Hello,

Very basic question. I would like to share a directory on the samba server. So, I ougth to add the following: 

```
[dir_user_X]
   comment = Directory user X
   path = /mnt/sdb2
   guest ok = no
   read only = no
```

Is this method above the correct one?
The problem is that all users could "see" this share, and it is not only for a single given username of samba. 

Is there maybe another method?

Kind regards



# Sample
```


# Un-comment the following and create the netlogon directory for Domain Logons
# (you need to configure Samba to act as a domain controller too.)
;[netlogon]
;   comment = Network Logon Service
;   path = /home/samba/netlogon
;   guest ok = yes
;   read only = yes

# Un-comment the following and create the profiles directory to store
# users profiles (see the "logon path" option above)
# (you need to configure Samba to act as a domain controller too.)
# The path below should be writable by all users so that their
# profile directory may be created the first time they log on

;[profiles]
;   comment = Users profiles
;   path = /home/samba/profiles
;   guest ok = no
;   browseable = no
;   create mask = 0600
;   directory mask = 0700

[Home Directory]
  comment = Home Directories
  browseable = no
  valid users = %S
  writeable = yes
  create mode = 0600
  directory mode = 0700


[printers]
   comment = All Printers
   browseable = no
   path = /var/spool/samba
   printable = yes
   guest ok = no
   read only = yes
   create mask = 0700

# Windows clients look for this share name as a source of downloadable
# printer drivers
[print$]
   comment = Printer Drivers
   path = /var/lib/samba/printers
   browseable = yes
   read only = yes
   guest ok = no
# Uncomment to allow remote administration of Windows print drivers.
# You may need to replace 'lpadmin' with the name of the group your
# admin users are members of.
# Please note that you also need to set appropriate Unix permissions
# to the drivers directory for these users to have write rights in it
;   write list = root, @lpadmin

# A sample share for sharing your CD-ROM with others.
;[cdrom]
;   comment = Samba server's CD-ROM
;   read only = yes
;   locking = no
;   path = /cdrom
;   guest ok = yes

# The next two parameters show how to auto-mount a CD-ROM when the
#	cdrom share is accesed. For this to work /etc/fstab must contain
#	an entry like this:
#
#       /dev/scd0   /cdrom  iso9660 defaults,noauto,ro,user   0 0
#
# The CD-ROM gets unmounted automatically after the connection to the
#
# If you don't want to use auto-mounting/unmounting make sure the CD
#	is mounted on /cdrom
#
#;   preexec = /bin/mount /cdrom
#;   postexec = /bin/umount /cdrom

#[workdisk]
#
#   comment = Samba server's Work
#   writable = yes
#   locking = no
#   path = /workdisk
#   public = yes


# The next two parameters show how to auto-mount a CD-ROM when the	
#   cdrom share is accesed. For this to work /etc/fstab must contain
#   an entry like this:
#
#       /dev/scd0   /cdrom  iso9660 defaults,noauto,ro,user   0 0
#
# The CD-ROM gets unmounted automatically after the connection to the
#
# If you don't want to use auto-mounting/unmounting make sure the CD
#   is mounted on /cdrom
#
;   preexec = /bin/mount /cdrom
;   postexec = /bin/umount /cdrom

```

---

### Post by Morbius1 on 2013-02-03
If I understand your original post you want this share to be accessible to only one user and not everyone with a samba password. If that is correct then change your share definition to this:
> [dir_user_X]    
comment = Directory user X 
   path = /mnt/sdb2    
guest ok = no    
read only = no
[COLOR=Blue]**valid users = morbius**[/COLOR]*Change morbius to the user who you want to grant access.*

---

### Post by honeybear on 2013-02-06
> **Morbius1 said:**
> If I understand your original post you want this share to be accessible to only one user and not everyone with a samba password. If that is correct then change your share definition to this:
*Change morbius to the user who you want to grant access.*

Thank you! I use your method now.

Btw, would you if it is possible to disable the 
account of the given and to keep it samba working.

likely yes.
With changing /etc/passwd might be the thing to modify
and keep the samba running as normally with:
path = /home/%S

---

