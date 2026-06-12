---
title: "Understanding Linux permissions."
date: 2020-03-13
forum: New to Ubuntu
---

### Post by elsmandino2 on 2020-03-13
Hello.

I know that this subject has been done to death, but it is the one thing that seems to prevent me from really getting on with Linux.

Can I just check that the following is true, please:

Say I have the following directory on my server (192.168.1.40)

 **/NFSShare/ ** 

and this directory has its own permissions - e.g. 775.

I then share the folder with the following in /etc/exports/

**/NFSshare/ 192.168.1.0/24(rw,sync,no_root_squash)**

Does that mean that if any client PC mounts the NFS share, the NFS share permissions apply first and then the permissions of the folder itself.

For example, if the folder has a permission of 777 (so anybody can write to it), but it is shared via NFS with (ro, sync,no_root_squash), does that mean that a client is still prevented to from writing to it?

---

### Post by TheFu on 2020-03-13
A read-only NFS export will override any other permissions, just like any other mount option for local or remote storage.

Permissions aren't just about the 32-bits, the owner, group, "other" and ACLs matter. Also, less talk, show the **ls -al** for the files and parent directory.
Please, never, ever, ever, use 777 permissions.

 /NFSshare/ 192.168.1.0/24(rw,sync,no_root_squash)
should probably be:
```
/NFSshare          192.168.1.0/24(rw,sync,no_root_squash)
```
and no way would I allow root from any system on the subnet to have root control. That's terrible security, especially if there's any wifi on that subnet.

I specifically list each NFS client machine in the exports.  And putting a "sync" in the options will really impact performance.

Here's an example:
```
/D/ebooks/Library       nextcloud(ro,async,root_squash) 
```
I don't trust nextcloud (DNS name) to have read-write access to my Calibre ebook Library.

The only real trick to NFS is to ensure that uid/gid numbers match across all clients and the server for any file/dir objects exported.

---

### Post by elsmandino2 on 2020-03-19
Thank you for this - I think I am starting (albeit slowly) to get the hang of this.


Would it be at all possible to help me with a practical example, please (I tend to find that I learn best by actually doing it)?


I have a home network:


My desktop Ubunt PC is john@192.168.1.15 - acting as my client.


I have just set up Raspbian on an old RaspberryPi - pi@192.168.1.50 - acting as my host.


On 192.168.1.50, I have created a directory to be shared - /NFSShare


On 192.168.1.15, I have created a directory (/mnt/NFSShare), which I want to use to mount "NFSShare" on the server.


What would you personally do set up the share between the server and the host?

---

### Post by TheFu on 2020-03-19
A rPi is a terrible NFS server.  USB2 to slow.  Networking is shared with the internal USB bus, so access to the storage competes for network bandwidth.  So, first, I'd get a better NFS server. Doesn't need to be much. My main NFS server is a $120 "server" with a Pentium G3258 CPU (65W max) and multiple GigE NICs. It has 32TB of storage connected, but started out with just 1TB as an internal disk. Now it has 6 internal disks and 4 disks in an external eSATA array.  For backup storage, there are a few USB3 external HDDs.

No way, no how would I mount anything under /media/ or /mnt/ for NFS.  The _File System Hierarchy Standards_ say those are for temporary mounts only. /mnt/ is for admin work.  /media/ is for CDROMs, DVDs, and temporary USB stuff.

Today, I'd use systemd automount:
[https://ubuntuforums.org/showthread.php?t=2437500&p=13935156#post13935156](https://ubuntuforums.org/showthread.php?t=2437500&p=13935156#post13935156)
Previously, I used autofs, but systemd automount is already there and works fine from what I've seen the last month or 2.

And I'd make it so hostnames are resolved on each system. With just two, I'd edit the /etc/hosts file on each so they know about each other. No more need to use IP addresses. This assumes both have static IPs, which all devices that are yours on a home network should.  Guest devices should be on a completely separate guest network that doesn't have **any** access to the main home network.  It is also a good place to put IoT devices.

IMHO.

---

