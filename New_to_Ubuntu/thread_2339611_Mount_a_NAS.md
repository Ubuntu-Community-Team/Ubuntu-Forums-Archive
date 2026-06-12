---
title: "Mount a NAS"
date: 2016-10-10
forum: New to Ubuntu
---

### Post by pleaseletthisusernamework on 2016-10-10
Hello, thank you for your help in advance.

I am brand new to Ubuntu so please be gentle. I'm trying to find a really straight forward guide on how to mount a NAS drive. I am using Ubuntu 16.04 on a PC used as a Plex Server. I can see my NAS drive and access all my media through the 'Files' button but it can't be seen through Plex. 

According to the Plex forum "For Ubuntu to actually access (mount) your NAS shares,  NFS or SMB sharing must be enabled **and** you must mount (see man mount.nfs or man mount.cifs for details on how) before the directories can be seen by Plex."

Can anyone point me to a simple walkthrough of how to do this?

---

### Post by TheFu on 2016-10-10
Welcome to the forums.

It isn't clear to me where the storage is and which system(s) you want to see it on.
NFS is pretty simple, when you follow the rules.
a) userids need to be identical on all systems ... usually this is only important for user accounts, but for plex, you'll want to make certain that plex userid and groupid are identical across all the systems.
b) NFS has a server and a client.  The server must be installed on the system SHARING the storage over the network. The client needs to be installed on every client system. The nfs-server is a kernel module, so you'll need to load that module (or reboot).  There might be 1 other dependence - rpc-something. A guide should spell that out if it isn't handled automatically.
c) On the NFS server, you need to setup the "exports."  This is a file.
d) Depending on how you'd like to mount (there are multiple ways), you can just edit the fstab on each client to mount the storage where you like.
e) If you have a firewall running, you'll need to open the ports on the server ... think there are a few for rpc and nfs.
f) If you use NFSv3, there isn't any security beyond what is in the "exports" file. The configuration **is** the security along with using static IPs for all servers and clients.  I've never attempted to do it with DHCP IP addresses. Seems like that would be a hassle to me.  NFSv3 should only be used on the same, secured, subnet.
g) If you use NFSv4, things get more complicated since Kerberos is used. This is server-to-server PKI-based authentication and additional encryption is possible. People do share storage over the internet, but I wouldn't without a full VPN in addition.

I wouldn't use NFS over wifi. A very stable connection is needed.

So, with that high-level info, searching for "nfs ubuntu" will find a how-to guide or 20.  Prefer the ones with *.ubuntu.com locations.

After you get everything mounts, be certain to ensure that plex has read permissions to all the storage. It doesn't need to be the owner, but the groupid should be plex with read.  It is handy to use the g+s permission on all directories for media, so plex gid is automatically set.

Anyway, hope this is helpful.

---

