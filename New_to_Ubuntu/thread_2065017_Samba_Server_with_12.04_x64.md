---
title: "Samba Server with 12.04 x64"
date: 2012-09-30
forum: New to Ubuntu
---

### Post by GrumpyBum on 2012-09-30
I am trying to get a Samba file server running at home and every guide I find makes this look straight forward. The problem is that the Samba configuration directory is read only and I cannot change this so cannot configure Samba :(

1. I have selected Samba as an option installing Ubuntu 12.04 Server
2. I have tried to configure the smb.conf using nano but cannot write due to read only.
3. I cannot change the directory from read only, even if I stop the service.

```
arnie@sambafs:~$ ls -l /etc/samba
total 20
-rw-r--r-- 1 root root     0 Sep 30 15:49 dhcp.conf
-rw-r--r-- 1 root root     8 Jun  8 23:14 gdbcommands
-rw-r--r-- 1 root root 12464 Sep 30 15:44 smb.conf

```

```
root@sambafs:~# chmod ugo+rwx /etc/samba/smb.conf
chmod: changing permissions of `/etc/samba/smb.conf': Read-only file system
root@sambafs:~# ls -l /etc/samba/smb.conf
-rw-r--r-- 1 root root 12464 Sep 30 15:44 /etc/samba/smb.conf

```

Can anyone help, please. All I want this server to do is run Samba so that I can have a file server at home.
This is running on XenServer 6 and an HP MicroServer.
I can confidant that I can get this running if I can only edit the smb.conf file as per online based instructions.

---

### Post by GrumpyBum on 2012-09-30
Hi All, it looks like everything I did above was okay and committed on a server reboot. I am wondering if this is because I am running 2 Virtual Machines of a SATA RAID1? or is this a new thing with 12.04 since 10.04?

---

