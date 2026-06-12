---
title: "fstab stopped working and NAS will not mount"
date: 2014-02-19
forum: New to Ubuntu
---

### Post by skeil on 2014-02-19
Hi. I have Ubuntu mint 14 Nadia. We have an iomega NAS. I eventually managed to get the fstab right and it mounted all the shares for both the ubuntu machine we have (the other runs mint 13.?)

Booted today and the mint 14 Nadia has not mounted the shares and i cannot mount them by commandline either 
```
sudo mount -a 
```
and nothing happens after inputting the password.

The mint 13 machine that has exactly the same fstab and is still mounting the shares as before.
The fstab is 

```
//192.168.0.101/Mail /media/NAS/Mail cifs guest,uid=1000,gid=1000,rw,iocharset=utf8,_netdev,file_mode=0777,dir_mode=0777,auto 0 0
```

The syslog shows
```
CIFS VFS: cifs_mount failed w/return code = -101
 CIFS VFS: Error connecting to socket. Aborting operation 
```

Tried rebooting, the problem still remains.

Has anyone got any ideas. I hope i have put the code in correctly, not done this before. Many thanks for all those who post replies - they helped me get this working first time around and solve many other issues.

---

### Post by ian-weisser on 2014-02-19
Error code 101 usually means the network is not available when mount tries to connect.
Check your /var/log/syslog for network availability before network-drive mounting.

---

