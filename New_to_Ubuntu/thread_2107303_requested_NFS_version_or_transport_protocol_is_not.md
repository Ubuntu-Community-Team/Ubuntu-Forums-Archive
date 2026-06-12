---
title: "requested NFS version or transport protocol is not supported"
date: 2013-01-21
forum: New to Ubuntu
---

### Post by djoshea on 2013-01-21
I'm running 12.10 and trying to mount an NFS v3 share. I'm run into problems 

I've setup by running:
```

sudo apt-get install nfs-common portmap nfs-kernel-server
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Note, selecting 'rpcbind' instead of 'portmap'
nfs-common is already the newest version.
nfs-kernel-server is already the newest version.
rpcbind is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.


```
which strikes me as interesting only since rpcbind replaces portmap.

Here's the problem. When I try to mount:
```

sudo mount -v -t nfs -o vers=3,nvsvers=3 server:/exports/sww sww
mount.nfs: timeout set for Mon Jan 21 10:40:11 2013
mount.nfs: trying text-based options 'vers=3,nvsvers=3,addr=192.168.100.10'
mount.nfs: prog 100003, trying vers=3, prot=6
mount.nfs: portmap query retrying: RPC: Program not registered
mount.nfs: prog 100003, trying vers=3, prot=17
mount.nfs: portmap query failed: RPC: Program not registered
mount.nfs: requested NFS version or transport protocol is not supported

```

When I try to showmount either locally or on server (also ubuntu but 10.04.4):
```
clnt_create: RPC: Program not registered
```

And following other threads I've found while searching, when I try to check the status of nfs services:
```
sudo service nfs status
nfs: unrecognized service

sudo service nfs-common status
nfs-common: unrecognized service

```

I don't have any firewall rules setup:
```
sudo iptables --list
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination     
```

And finally, rpcinfo returns:
```
rpcinfo -p
   program vers proto   port  service
    100000    4   tcp    111  portmapper
    100000    3   tcp    111  portmapper
    100000    2   tcp    111  portmapper
    100000    4   udp    111  portmapper
    100000    3   udp    111  portmapper
    100000    2   udp    111  portmapper
    100024    1   udp  42608  status
    100024    1   tcp  57112  status
    100003    2   tcp   2049  nfs
    100003    3   tcp   2049  nfs
    100003    4   tcp   2049  nfs
    100227    2   tcp   2049
    100227    3   tcp   2049
    100003    2   udp   2049  nfs
    100003    3   udp   2049  nfs
    100003    4   udp   2049  nfs
    100227    2   udp   2049
    100227    3   udp   2049
    100021    1   udp  44623  nlockmgr
    100021    3   udp  44623  nlockmgr
    100021    4   udp  44623  nlockmgr
    100021    1   tcp  56561  nlockmgr
    100021    3   tcp  56561  nlockmgr
    100021    4   tcp  56561  nlockmgr
    100005    1   udp  56180  mountd
    100005    1   tcp  33438  mountd
    100005    2   udp  41054  mountd
    100005    2   tcp  35206  mountd
    100005    3   udp  36640  mountd
    100005    3   tcp  56588  mountd

```

Any ideas what's going on with RPC and NFS v3?

---

### Post by luvshines on 2013-01-21
I have couple of dump questions

- Did you try running showmount -e <server-ip> ?

- On the server, /etc/init.d/nfs-kernel-server status

- Where did you run rpcinfo -p and iptables -L ?

- From the client, check if portmapper on the server is reachable```
nc -zv <server-ip> 111
```

---

### Post by nathrich on 2013-02-07
I'm getting same error with a specific server (which happens to be running Windows Server). However, NFS was working fine with this server last week before we had a power failure. Also, NFS is working fine with other servers. And this Windows Server has NFS working fine for other clients not running ubuntu. 

Problem client running Ubuntu 12.04.1 LTS.

---

### Post by jrda on 2013-05-12
Have the same Problem with my QNAP NAS. The Workaround was to disable and enable NFS in the Webinterface of my QNAP again.

---

### Post by jimlocke on 2014-05-04
> **jrda said:**
> Have the same Problem with my QNAP NAS. The Workaround was to disable and enable NFS in the Webinterface of my QNAP again.

Thank you for posting, jrda!  I had the same issue and fix.  Not sure how quickly I would have thought to try this, however I've seen before where after firmware upgrades a service shows as running but it's not running correctly.

---

