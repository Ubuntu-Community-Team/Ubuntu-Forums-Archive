---
title: "NFS setup"
date: 2013-04-06
forum: New to Ubuntu
---

### Post by lakz on 2013-04-06
Hi,
I'm getting this when I run **sudo exportfs -a**
> exportfs: No options for to NFS: suggest NFS(sync) to avoid warning
exportfs: /etc/exports [1]: Neither 'subtree_check' or 'no_subtree_check' specified for export "NFS:to".
  Assuming default behaviour ('no_subtree_check').
  NOTE: this default has changed since nfs-utils version 1.0.x


exportfs: No options for to clients.: suggest clients.(sync) to avoid warning
exportfs: /etc/exports [1]: Neither 'subtree_check' or 'no_subtree_check' specified for export "clients.:to".
  Assuming default behaviour ('no_subtree_check').
  NOTE: this default has changed since nfs-utils version 1.0.x


exportfs: duplicated export entries:
exportfs:       clients.:to
exportfs:       NFS:to
exportfs: No options for to See: suggest See(sync) to avoid warning
exportfs: /etc/exports [1]: Neither 'subtree_check' or 'no_subtree_check' specified for export "See:to".
  Assuming default behaviour ('no_subtree_check').
  NOTE: this default has changed since nfs-utils version 1.0.x


exportfs: duplicated export entries:
exportfs:       See:to
exportfs:       NFS:to
exportfs: /etc/exports:1: syntax error: bad option list
exportfs: Failed to stat to: No such file or directory
lakz@ubuntuserver:~$ sudo nano /etc/exports
lakz@ubuntuserver:~$ sudo exportfs -a^C
lakz@ubuntuserver:~$ sudo exportfs -a
exportfs: No options for to NFS: suggest NFS(sync) to avoid warning
exportfs: /etc/exports [1]: Neither 'subtree_check' or 'no_subtree_check' specified for export "NFS:to".
  Assuming default behaviour ('no_subtree_check').
  NOTE: this default has changed since nfs-utils version 1.0.x


exportfs: No options for to clients.: suggest clients.(sync) to avoid warning
exportfs: /etc/exports [1]: Neither 'subtree_check' or 'no_subtree_check' specified for export "clients.:to".
  Assuming default behaviour ('no_subtree_check').
  NOTE: this default has changed since nfs-utils version 1.0.x


exportfs: duplicated export entries:
exportfs:       clients.:to
exportfs:       NFS:to
exportfs: No options for to See: suggest See(sync) to avoid warning
exportfs: /etc/exports [1]: Neither 'subtree_check' or 'no_subtree_check' specified for export "See:to".
  Assuming default behaviour ('no_subtree_check').
  NOTE: this default has changed since nfs-utils version 1.0.x


exportfs: duplicated export entries:
exportfs:       See:to
exportfs:       NFS:to
**exportfs: /etc/exports:1: syntax error: bad option list**
**exportfs: Failed to stat to: No such file or directory**

Here's my /etc/exports :

> # /etc/exports: the access control list for filesystems which may be exported
                to NFS clients.  See exports(5).
#
# Example for NFSv2 and NFSv3:
# /srv/homes       hostname1(rw,sync,no_subtree_check) hostname2(ro,sync,no_subtree_check)
#
# Example for NFSv4:
# /srv/nfs4        gss/krb5i(rw,sync,fsid=0,crossmnt,no_subtree_check)
# /srv/nfs4/homes  gss/krb5i(rw,sync,no_subtree_check)
#


/nfstest 192.169.1.1(rw,sync,no_subtree_check)

The /nfstest directory has been created and is visible. What is going on?

This is my second day using Linux, so I'm completely new to all this. I'm on a virtualized (ESXi) Ubuntu Server 12.04.2 LTS. I want to share a directory so it can be accessible to my OpenELEC HTPC and other Windows PC on the network as well.

---

### Post by r-senior on 2013-04-06
Have you wrapped that first comment line by accident? I think it's "to NFS clients" that it is objecting to. (A '#' comment only extends to the end of the line).

```
# /etc/exports: the access control list for filesystems which may be exported
[COLOR="#FF0000"]to NFS clients. See exports(5).[/COLOR]
#
...

```

---

### Post by lakz on 2013-04-06
That must be it! Yeah, I don't know how that happened... Now when I run **sudo exportfs -a **nothing happens. Is it normal?
Also, is **[COLOR=#000000]*/nfstest 192.169.1.1(rw,sync,no_subtree_check)*[/COLOR]** appropriate to share /nfstest? 192.168.1.1 is my router.

---

### Post by r-senior on 2013-04-06
Linux commands often output nothing if they worked OK. You can query the exports with:

```
showmount -e
```

If you specify a single IP address, that's the only client that can mount that export. That is probably not what you want if you have multiple clients on the network. You could use an address/netmask in place of the IP address:

```
192.168.1.0/255.255.255.0
```

This gives access for IP addresses 192.168.1.0 through 192.168.1.255. 

There are other ways to specify wildcards, refer to 

```
man 5 exports
```

---

### Post by lakz on 2013-04-06
Thanks a bunch. I have now access to the folder on Windows 7! That was relatively painless.

I used a little software named Neko to mount the folder on the Windows side... Even though it works just fine, I'd like to ditch that third party app (I know, we're getting off limits here :), but I thought someone might know). The command is supposed to be :

> [COLOR=#000000][FONT=courier new]mount [options] //nfs-server-unc-name/share-name [drive letter][/FONT][/COLOR]

So in my case, what should the command look like?

[COLOR=#000000][FONT=courier new]**mount //192.168.1.121/nfstest k:** ?[/FONT][/COLOR]

---

