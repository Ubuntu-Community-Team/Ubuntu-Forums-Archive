---
title: "NFS server configuration problem and questions"
date: 2014-02-07
forum: New to Ubuntu
---

### Post by macrolyte on 2014-02-07
Hello, All.
I'm having an issue configuring NFS; the client is a piece of software, which uses NFS, that needs to access the / file system on the same box it's running on. I'm running **Gutsy**, amd64. My configuration:

```
[INDENT]$dpkg -l nfs-common
ii  nfs-common     1:1.1.1~git-20
$dpkg -l nfs-user-server
ii  nfs-user-serve 2.2beta47-23
/       10.0.0.2(rw,no_root_squash,sync,no_subtree_check) ;; /etc/exports
$sudo showmount -e localhost
Export list for localhost:
/ 10.0.0.2
[/INDENT]

```

When I attempt to configure the software it needs to write to a folder in the user's home folder, I gave the folder 777 permission, and the software says 'error: read only file system'. I immediately tried to download a file and was able to save it... 

My additional questions:

[INDENT]I see that there is a kernel module called 'nfsd'; should I be loading this as well?

```
cat /boot/config-2.6.22-14-generic | grep NFS
CONFIG_NFSD=m
``` 

I see that there is **nfs-kernel-server package**; is this related to the module 'nfsd' and should I have installed it instead?
[/INDENT]


I'm very new to Ubuntu, and have already had fun locking myself out my installation, (thank God I installed blackbox!). So, before I kack something else up, I'd really appreciate some help. Thanks.

---

### Post by macrolyte on 2014-02-07
Can anybody help?

---

### Post by Iowan on 2014-02-07
From the [Posting Guidelines]("http://ubuntuforums.org/showthread.php?t=2158945"):
>     Do not bump your thread more than once in any 24 hour period. Consider waiting longer than that before bumping - this may help to catch the attention of users outside of your timezone.
I presume you realize how outdated Gutsy is...

---

### Post by macrolyte on 2014-02-07
Sorry about the 'bump', didn't quite know the etiquette, I'll wait a couple of days from now on. Unfortunately the software I'm trying to use requires that specific OS. Believe me, I'd love to use **Precise** or better, but I'm stuck with the constraints that I'm under.

---

### Post by brokenhachi on 2014-02-07
what does your /etc/exports look like? nfs is running i assume? ```
sudo /etc/init.d/nfsd status
```

---

### Post by macrolyte on 2014-02-07
the package I'm using is nfs-user-server version 2.2beta47-23
```
[INDENT]/.
/etc
/etc/init.d
/etc/init.d/nfs-user-server
/usr
/usr/share
/usr/share/man
/usr/share/man/man5
/usr/share/man/man5/exports.5.gz
/usr/share/man/man8
/usr/share/man/man8/rpc.nfsd.8.gz
/usr/share/man/man8/rpc.mountd.8.gz
/usr/share/doc
/usr/share/doc/nfs-user-server
/usr/share/doc/nfs-user-server/BUGS
/usr/share/doc/nfs-user-server/HALL_OF_FAME
/usr/share/doc/nfs-user-server/README.HISTORIC.gz
/usr/share/doc/nfs-user-server/README.CDF
/usr/share/doc/nfs-user-server/changelog.gz
/usr/share/doc/nfs-user-server/TODO
/usr/share/doc/nfs-user-server/copyright
/usr/share/doc/nfs-user-server/NEWS.gz
/usr/share/doc/nfs-user-server/README.gz
/usr/share/doc/nfs-user-server/changelog.Debian.gz
/usr/sbin
/usr/sbin/rpc.mountd
/usr/sbin/rpc.nfsd
[/INDENT]

```

The rpc.nfsd doesn't have status as an option. My /etc/exports

```


/       10.0.0.2(rw,no_root_squash,sync,no_subtree_check) ;; /etc/exports

```
```

$ rpcinfo -p
   program vers proto   port
    100000    2   tcp    111  portmapper
    100000    2   udp    111  portmapper
    100024    1   udp  32768  status
    100024    1   tcp  48412  status
    100003    2   udp   2049  nfs
    100003    2   tcp   2049  nfs
    100005    1   udp    698  mountd
    100005    2   udp    698  mountd
    100005    1   tcp    699  mountd
    100005    2   tcp    699  mountd

```

This has me completely stumped.

---

### Post by macrolyte on 2014-02-08
On a hunch, I decided to uninstall nfs-common and nfs-user-server packages and installed:

```
[INDENT=2]nfs-common 1.1.2-2
nfs-kernel-server 1.1.2-2
[/INDENT]
 
```

for **Hardy**! Had to get the packages and depends from Launchpad. After that all I tried was:

```
[INDENT]exportfs -a
[/INDENT]

```

And it worked. The software I need to use is now configured and I can now setup start up scripts for boot time. Thanks brokenhachi for your help. I kinda thought that packages were independent of the OS, now I know for sure.

---

