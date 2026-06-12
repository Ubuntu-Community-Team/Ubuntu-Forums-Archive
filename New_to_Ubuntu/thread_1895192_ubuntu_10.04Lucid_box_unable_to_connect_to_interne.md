---
title: "ubuntu 10.04Lucid box unable to connect to internet"
date: 2011-12-14
forum: New to Ubuntu
---

### Post by vej1lr on 2011-12-14
Hi,

We have a ubuntu 10.04 Lucid release box & unable to connect to the internet from this box. While all other machines in the same network has no issues. Can someone suggest what could be wrong with this. Here is the output from dmesg.

------------------------
device eth0 left promiscuous mode
eth0: no ipv6 routers present
nfsd: last server has exited, flushing export cache
svc: failed to register lockdv1 RPC service (errno 97)
NFSD: Using /var/lib/nfs/v4recovery as the NFSv4 state recovery directory
NFSD: starting 90-second grace period
------------------------

I did notice that tcpdump is running, I stopped that & then eth0 left non-promiscuous mode. Still ping 8.8.8.8 doesn work.
this machine is a NFS server. Obviously there are errors about NFS, but the NFS exported directory is accessible from all clients. After googling about the error, got to know that disabling IPv6 would help in getting rid of these NFS-errors. But does it help in getting the machine connecting to internet?

Thanks in advance

---

