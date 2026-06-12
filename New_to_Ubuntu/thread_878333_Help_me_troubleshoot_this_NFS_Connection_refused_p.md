---
title: "Help me troubleshoot this NFS Connection refused problem"
date: 2008-08-02
forum: New to Ubuntu
---

### Post by ant2ne on 2008-08-02
The error that I get from the client OLPC laptop (running xfce4 and host name of xo-0d-68-AD) is 
```
mount 2ne-buntu:/media/md3/shares/open /mnt/net.open
mount: mount to NFS server '2ne-buntu' failed: System Error: Connection refused.
```

EXPORTS  This should be wide open
```
ant2ne@2ne-buntu:/media/md3/shares$ cat /etc/exports
# /etc/exports: the access control list for filesystems which may be exported
#               to NFS clients.  See exports(5).
#
# Example for NFSv2 and NFSv3:
# /srv/homes       hostname1(rw,sync) hostname2(ro,sync)
#
# Example for NFSv4:
# /srv/nfs4        gss/krb5i(rw,sync,fsid=0,crossmnt)
# /srv/nfs4/homes  gss/krb5i(rw,sync)

/media/md3/shares/open 192.168.1.1/24(rw,no_root_squash,async)
/media/md3/shares/open xo-0d-68-AD(rw,no_root_squash,async)

```

FS permissions. As you can see, they are wide open and the client should be able to read via NFS.
```
ant2ne@2ne-buntu:/media/md3/shares$ ls -l
total 24
drwxrwxrwx  9 ant2ne sambausers 4096 2008-07-28 18:37 open

```

FIREWALL
And in firestarter, I have a policy for "Allow connections from host" including the clients IP, and I have an "Allow Service" for NFS allowing everyone.

the /media/md3/shares/open directory is also being shared by samba. I have windows machines that need to access the same files as my OLPC. The OLPC can run samba, but it has no cifs or smbfs support in its stupid kernel. I hope NFS and SAMBA are not in conflict trying to share this directory.

note: once I get the clients to connect, I will then work on trimming up the access.

What is the next step in troubleshooting this?

Thanks

---

### Post by mattismyname on 2008-08-02
I would check to see if you can mount the filesystem from the local host.  That could help rule out a firewall rule.

Also, do you have an NFS server running?  Just editing the exports file will not be enough to guarantee an NFS server is actually running.

[https://help.ubuntu.com/8.04/serverguide/C/network-file-system.html](https://help.ubuntu.com/8.04/serverguide/C/network-file-system.html)

---

### Post by spoonernash on 2008-08-02
I'll give this a try.

On the server, you did run exportfs -r, right?
Does exportfs -v show the exports?

Is nfs installed on the client? I think the package is nfs-common.

---

### Post by ant2ne on 2008-08-02
```
ant2ne@2ne-buntu:/media/md3/shares$ sudo /etc/init.d/nfs-kernel-server start
 * Exporting directories for NFS kernel daemon...                 exportfs: /etc/exports [2]: Neither 'subtree_check' or 'no_subtree_check' specified for export "192.168.1.1/24:/media/md3/shares/open".
  Assuming default behaviour ('no_subtree_check').
  NOTE: this default has changed since nfs-utils version 1.0.x

exportfs: /etc/exports [3]: Neither 'subtree_check' or 'no_subtree_check' specified for export "xo-0d-68-AD:/media/md3/shares/open".
  Assuming default behaviour ('no_subtree_check').
  NOTE: this default has changed since nfs-utils version 1.0.x

                                                           [ OK ]
 * Starting NFS kernel daemon                              [ OK ] 

```

```
ant2ne@2ne-buntu:/media/md3/shares$ exportfs -v
/media/md3/shares/open
		hit-nxdomain.opendns.com(rw,async,wdelay,no_root_squash,no_subtree_check)
/media/md3/shares/open
		192.168.1.1/24(rw,async,wdelay,no_root_squash,no_subtree_check)
ant2ne@2ne-buntu:/media/md3/shares$ 

```

"mount the filesystem from the local host"
```
ant2ne@2ne-buntu:/media/md3/shares$ sudo mount 2ne-buntu:/media/md3/shares/open ~/tmp

```the last command just hangs. No error no nothing

---

### Post by spoonernash on 2008-08-02
I see opendns.com in the output of exportfs -v. Do you have a dns issue? What is the ip address of your client?

---

### Post by ant2ne on 2008-08-03
I use DDWRT as my DNS server. my NFS server has as static IP. The DDWRT resolves names to any static IPs. I can ping the NFS server by name from the client(s).

The DDWRT box IP is 192.168.1.1
The NFS servers IP is 192.168.1.100
The NFS Client IP is 192.168.1.137

---

### Post by ant2ne on 2008-08-03
I can't help but think this is an unauthenticated user issue. How does NFS authenticate users?

---

### Post by mattismyname on 2008-08-03
The message "Connection refused" leads me to believe it is not an authentication issue.  "Connection refused" is a very standard message which means one program tried to establish a TCP/IP connection to a server, but something (firewall, OS, no server running) caused the connection to be refused.

---

### Post by spoonernash on 2008-08-03
I think your /etc/exports needs to be this only:

/media/md3/shares/open 192.168.1.0/24(rw,no_root_squash,async)

---

