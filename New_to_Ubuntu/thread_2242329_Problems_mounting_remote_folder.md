---
title: "Problems mounting remote folder"
date: 2014-09-01
forum: New to Ubuntu
---

### Post by informatique-p on 2014-09-01
I'm having a problem mounting a folder called NAS in our  Ubuntu 14LTS and with a folder located in one of our NAS (/mnt/NAS).  Both are accessible and they can ping each other. I followed these steps  in order to automount the NAS destination folder:
  
[LIST=1]
[*]Create folder NAS at /mnt/, using mkdir /mnt/NAS
[*]Add the following line in /etc/fstab:  sshfs#bmtechnicien@XXX.XXX.X.XX:/mnt/array1/Proton2 /mnt/NAS fuse  delay_connect,idmap=user,uid=1000,gid=1000,umask=0,allow_other,_netdev,workaround=rename  0 0

[*]Use the following command: mount -a . I did not get any error message and proceeded to go to the mounted folder (cd /mnt/NAS).
[/LIST]
  Problems started: It first says it doesn't find it Then, when doing an ls in /mnt it doesn't find it at all. Finally, when doing an ls -la on /mnt folder, I saw that the directory  NAS has no rights at all and is completely messed up: d?????????  ? ?    ?        ?            ? NAS
  I tried to manually mount the same destination folder on another Ubuntu server and it worked, with the following command:  sshfs bmtechnicien@192.168.1.74:/mnt/array1/Proton2 /mnt/NAS
  If I try to delete the NAS folder in /mnt, with rm -r NAS, it says I have not the rights although I'm as root.
  How could I correct this problem?

---

### Post by TheFu on 2014-09-01
So ....  welcome to the forums.   That is 1 heck of a post for a first 1 here.

Pick a protocol and use it.  CIFS, NFS, SSHFS .... pick one.  Don't get them confused. They each have different capabilities and features.

I would strongly suggest using NFS, if the storage device supports it.  Unless there is wifi between the NAS and the server.

Root doesn't get root access to remote NFS storage by default. This is part of system security considerations.  The NAS would need to be configured to allow remote root to work.  Generally, it is a bad idea ... unless you need to run virtual machines from the storage.  **rm -r NAS** isn't just asking to delete the folder - it is asking to delete all the files on the the NAS too. Is that really what you wanted?  If the device is mounted to /mnt/NAS, umount it first, then use rmdir to delete the directory.

Different NAS devices have very different features and capabilities. Not all of them are good systems.

"automounting" is a specific way to mount storage - mostly [using autofs]("https://help.ubuntu.com/community/Autofs"). It doesn't use the fstab at all.

---

