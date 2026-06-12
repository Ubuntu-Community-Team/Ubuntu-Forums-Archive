---
title: "Not starting NFS kernel daemon: no support in current kernel."
date: 2016-09-05
forum: New to Ubuntu
---

### Post by davess2 on 2016-09-05
I did a fresh install of Ubuntu Server LTS 14.04.5 from CD.  I tried to install NFS server but got the following error:

```

root@Hermione:~# apt-get install nfs-kernel-server 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  nfs-kernel-server
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0 B/85.8 kB of archives.
After this operation, 525 kB of additional disk space will be used.
Selecting previously unselected package nfs-kernel-server.
(Reading database ... 40307 files and directories currently installed.)
Preparing to unpack .../nfs-kernel-server_1%3a1.2.8-6ubuntu1.2_amd64.deb ...
Unpacking nfs-kernel-server (1:1.2.8-6ubuntu1.2) ...
Processing triggers for man-db (2.6.7.1-1ubuntu1) ...
Processing triggers for ureadahead (0.100.0-16) ...
ureadahead will be reprofiled on next reboot
Setting up nfs-kernel-server (1:1.2.8-6ubuntu1.2) ...
 * Stopping NFS kernel daemon                                                                                                                                               [ OK ] 
 * Unexporting directories for NFS kernel daemon...                                                                                                                         [ OK ] 
 *** Not starting NFS kernel daemon: no support in current kernel.**

```

I finished the configuration per [https://help.ubuntu.com/14.04/serverguide/network-file-system.html](https://help.ubuntu.com/14.04/serverguide/network-file-system.html)

Here's my exports file:
```

# /etc/exports: the access control list for filesystems which may be exported to NFS clients.  See exports(5).
/export/Ollivanders    *(rw,sync,no_subtree_check,no_root_squash)

```

Here's my imapd.conf file:
```

[General]

Verbosity = 0
Pipefs-Directory = /run/rpc_pipefs
# set your own domain here, if id differs from FQDN minus hostname
Domain = local

[Mapping]

Nobody-User = nobody
Nobody-Group = nogroup

```

I'm unable to mount the export on another machine--the mount command just hangs.

After an internet search, I tried:
```

root@Hermione:~# modprobe nfsd
modprobe: ERROR: ../libkmod/libkmod.c:556 kmod_search_moddep() could not open moddep file '/lib/modules/4.4.0-34-generic/modules.dep.bin'

dave@Hermione:~$ ps -e | grep rpc
  511 ?        00:00:00 rpcbind
  520 ?        00:00:00 rpc.statd
dave@Hermione:~$ ps -e | grep nfs
dave@Hermione:~$ nfsstat -s
Error: No Server Stats (/proc/net/rpc/nfsd: No such file or directory). 

```

What am I missing?

---

### Post by SeijiSensei on 2016-09-05
I'm sorry to report that I cannot replicate your experience on a fresh build of Server 14.04.5 running in a VirtualBox VM.  I installed the base system from the ISO image, then ran "sudo apt-get install nfs-kernel-server", and everything worked as expected.  I didn't run "apt-get update" or otherwise refresh the repository lists.  I just installed nfs-kernel-server immediately upon rebooting the server.

I'm running kernel version 4.4.0-31-generic.  Running "lsmod" shows the usual suspects loaded like sunrpc.

---

### Post by davess2 on 2016-09-08
Thanks, SeijiSensei!  After your reply, I realized I did an apt-get update, so did a fresh install and it's now working.

---

