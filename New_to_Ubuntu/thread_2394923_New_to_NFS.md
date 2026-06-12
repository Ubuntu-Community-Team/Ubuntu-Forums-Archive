---
title: "New to NFS"
date: 2018-06-23
forum: New to Ubuntu
---

### Post by hughoranga on 2018-06-23
Hi All

I'm trying to share files on an external hard disk plugged in to my ubuntu 16.04 desktop. I would like to access media on it from my raspberry pi running OSMC (locally networked with a cable) and if I can, access files across my local network of other ubuntu machines. Because these are all linux based systems, I am trying to use nfs, rather than Samba, which I understand is more for windows. I find all the tutorials scary because I don't understand what I am sudoing, but I have been trying. In particular, I feel I don't really understand directory paths and how to substitute the thing that I am trying to do into the example in the tutorial. But I don't know what is going wrong.

Here is an outline of what I have attempted so far.

Set up the media server: I most recently have followed instructions I found here: [https://www.howtoforge.com/nfs-server-on-ubuntu-14.10](https://www.howtoforge.com/nfs-server-on-ubuntu-14.10)
             I tried to change the permissions of my hard disk. It is called Elvi, so I think its path is /media/hugh/Elvi. I used the command

                      sudo chown nobody:nogroup /media/hugh/Elvi
            I sudo nanoed into my /etc/exports and put a line in that said

                        /media/hugh/Elvi        192.168.2.1(rw,sync,root_squash,no_subtree_check)

192.168.2.1 is the IP address of my router. One earlier tutorial I used suggested this would let me share the files on the drive over my whole network, but now I can't find that tutorial any more. I have found the manual page for exports and read a little about the options in brackets there, but I am not at all sure about what I have there. 

I'm trying to post everything relevant, but I hope I don't overdo it. I'm pretty new to using forums at all.

I managed to SSH into my raspberry pi  - first time! In order to set up the client side, I have followed these instructions from OSMC

[https://discourse.osmc.tv/t/configuring-fstab-based-nfs-share-mounts/69953](https://discourse.osmc.tv/t/configuring-fstab-based-nfs-share-mounts/69953)

I can look for help client side there, as it is not ubuntu, but the guts of it is that after sudo nanoing my /etc/fstab I tried to check things were working by running

cd /mnt/Elvi

and I get a No such device message.

So I am appealing to forums for assistance. Sorry I have gotten long winded. Do I need to post more information?

---

### Post by TheFu on 2018-06-24
Did you format the HDD partition(s) to use a Linux file system, like ext4?   NTFS, which is what most HDDs ship with, shouldn't be used.  If you didn't re-format, that is the most likely problem.

Specifying the router IP is incorrect. The server should either allow the entire subnet or specify specific clients. I specify clients to prevent security issues - think of it as a whitelist technique. Just keep them on 1 line for the same export.

I use OSMC and NFS.

NFSv3 is easy.
NFSv4 is harder.

* Use ext4 (or any Linux file systems)
* uid/gui need to match across all systems. These are the numbers, not the usernames.  1000 --> 1000 for the uid, for the users and groups of the shared files/directories.  Don't worry about system uids matching.  It mainly becomes an issue with mixing OSX with other OSes, since OSX begins with 500, not 1000 for uids.
* Avoid placing NFS mounts under /media/ or /mnt/ directories. Those areas are for automatic mounts by the OS and temporary mounts while performing admin work, respectively.  Check the file system hierarchy standards for more info.

OSMC has 2 ways to deal with NFS. The default, standard way, and the OSMC GUI method. I've used both.  If you only want to share files with OSMC, then that is easier, but hides important details.  If you want to share across multiple unix systems, then I'd suggest using the same, manual, setup, across all clients.

If you confirm a Linux file system, then I'll look farther.

---

### Post by hughoranga on 2018-06-25
Thanks for your help, TheFu.

Yes, I have formatted the partition  on the hard drive to use ext4. I like the idea of being able to share  the volume over the whole network, but I'll try specifying the proper IP  addresses (rather than that of the router). I find it a fiddle to  figure out IP addresses, but hey, I'm just lazy. I did manage to get arp  or whatever working, so I should have thought of that myself.

The  rest of your message is harder for me to decode. If NFSv3 is easier,  I'm all for it, but I wasn't conscious of the difference. I don't know  what you mean by uid/gui needing to match. Gives me something to look  for, though! And I've started looking at

[https://help.ubuntu.com/community/LinuxFilesystemTreeOverview](https://help.ubuntu.com/community/LinuxFilesystemTreeOverview)

to  get started understanding the file system hierarchy standards, although  I see links that offer serious amounts of reading. I don't feel  confident with path name stuff, so this is good. Thanks. I didn't  realise I could avoid using /media or /mnt: I thought that was where it  just went. So heaps of food for thought, thanks. I will experiment again  in a few days time and let you know how I go just specifying the two IP  addresses of my ubuntu desktop (server) and OSMC (client). I won't be  moving fast, because dammit, I have a demanding day job, but I will get  there. If I can network these two using the standard method, hopefully I  will have learnt enough to share things across my network.

Many thanks for your comments.

---

### Post by TheFu on 2018-06-25
Quick tip.  Use static IPs on your home network for all non-portable devices.

[http://blog.jdpfu.com/2011/07/18/use-your-router-to-centralize-your-network-device-management](http://blog.jdpfu.com/2011/07/18/use-your-router-to-centralize-your-network-device-management) explains 1 method, but it is dependent on the router you have.

Static IPs and a well-managed /etc/hosts file on almost all systems will make NFS easier. It also helps with firewall rules across systems.  Android tablets, smartphones and IoT stuff get DHCP addresses that are "reserved", so they are effectively static on your LAN, but behave as expected in the world.

BTW, the linux file system hierarchy has a 200+ page standard, but really **only 1 table, on one page need be reviewed.** You know how standards have to cover every possible situation, but the main uses always starts very simple, and elegant, with just enough complexity to accomplish the core goals.

---

### Post by hughoranga on 2018-06-26
I have seen discussion of static IP addresses on my router's  documentation. I will look it up. That and your previous IP tip (not  using the router's IP address) might mean next time I get to look at  this, I may have had more luck.

But my burning question is, regarding the linux file system hierarchy, **which table on which page**?

---

### Post by TheFu on 2018-06-26
[https://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard](https://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard) is close enough.

---

### Post by hughoranga on 2018-07-09
Thanks for your help on this. I am still struggling. I have decided to  try following one of the guides that I have found, using their folders  and all, just as proof of concept, but still haven't got there. My major  question is how do I control the mount point, cos it always pops up in  /media. I'll keep chipping away, but I am going away for a while, so you  won't hear from me but I'll be back at it.

---

