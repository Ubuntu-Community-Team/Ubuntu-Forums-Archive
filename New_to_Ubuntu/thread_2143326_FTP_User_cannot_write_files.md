---
title: "FTP User cannot write files"
date: 2013-05-08
forum: New to Ubuntu
---

### Post by noncentz on 2013-05-08
Good Day Everyone,

I am new to ubuntu but I am really enjoying learning about the OS. I am testing a glusterfs storage solution and I cannot seem to get FTP to write to an NFS mount I setup. I set the mount point to a directory in the home folder of a test user I setup named 'gluster'. After setting up this user I am able to login to my server and I can navigate to the mount as well as create/edit/delete files OK.

-- mount -a @@ mount output --

glnode01.devnet.local:/gv0 on /home/gluster/GlusterTest type nfs (rw,vers=3,addr=192.168.1.210)

I would like to have access to this mount using FTP so I installed vsftpd on the server. Here are the relevant configurations for vsftpd.

-- /etc/vsftpd/vsftpd.conf

```

# Allow anonymous FTP? (Beware - allowed by default if you comment this out).
anonymous_enable=No
#
# Uncomment this to allow local users to log in.
local_enable=YES
#
# Uncomment this to enable any form of FTP write command.
write_enable=YES
#
# Default umask for local users is 077. You may wish to change this to 022,
# if your users expect that (022 is used by most other ftpd's)
local_umask=022
#
# If you want, you can arrange for uploaded anonymous files to be owned by
# a different user. Note! Using "root" for uploaded files is not
# recommended!
#chown_uploads=YES
#chown_username=root

# You may specify an explicit list of local users to chroot() to their home
# directory. If chroot_local_user is YES, then this list becomes a list of
# users to NOT chroot().
#chroot_local_user=YES
#chroot_list_enable=YES
# (default follows)
#chroot_list_file=/etc/vsftpd/chroot_list

```

After setting up the user I was able to connect to the FTP server using Filezilla which brought me to the users home directory. I am able to navigate all files on the server but I am not able to create files in any place other than the /home/ directory. I assumed since the NFS mount was located in the home directory I would be able to write files but this is not the case, yet when I login to the server I can write file perfectly. Because I cannot write files I assume this is a permissions error and I would really like access to all files in the system. I tried adding the user to sudoers but that has no effect.

The server I am connecting to is running centos6. The client I am using is ubuntu. I am not sure how to continue as I am unfamiliar with the OS as a whole. 

Any help would be greatly appreciate. --> noncentz

---

