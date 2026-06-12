---
title: "Folder permissions for Plex and Samba"
date: 2017-01-15
forum: New to Ubuntu
---

### Post by bjhutto on 2017-01-15
I have just moved to a new htpc running 16.04, and I am failing at getting folder access over my home network through Samba and also at getting the Plex media server to see my (local) media library.

The reason that I am posting these two issues together is because both problems deal with a single folder, titled 'share' and hosted on an external drive. My assumption is that the problem has to do with that folder's permissions. Also, it will likely be helpful to know, this folder is on a drive that I brought over from my old HTPC, which was running 14.04. Plex worked fine on the old machine, but I couldn't ever get Samba to work (with a lot of tinkering). 

This is what I have done today (I suppose there could be a conflict carried over from the old machine? would these settings override previous ones?):

for Plex
- I have added user 'plex' to my main group, MYGROUP
- I have kept user=plex in the plexmediaserver.service file but I've changed the group to MYGROUP
- I have set the permissions for the entire drive (which I'm assuming I own, as I'm the only user with a login) to 775

for Samba
- I have set the permissions for the 'share' folder (which is on the drive) to 777
- I have set the folder to 'share' (with full permissions) both in Samba and in Nautilus (oddly enough, the set permissions change according to whether or not I'm looking at them as a root user or not) 

I want my entire network to be able to see and access the 'share' folder but not the rest of the drive.

I am sure that the solution should be obvious, but I'm out of ideas. Any help you can offer will be greatly appreciated!

---

### Post by TheFu on 2017-01-16
What file system are the media file stored on?

777 should basically - NEVER - be used.  Please post the output of ls -l on the mount point and top level under it.  Only need to see a few directories, no files.  The most open directories should be are 775 and files 664.  750 and 640 respectively would be better, BTW. The group should be "plex" for all of them.

It isn't clear to me - what is samba for?  Is the plex machine the client or the server?  If the playback machines are not Windows, using NFS would be more efficient, provided the storage isn't NTFS.  NTFS brings all sorts of complexities to a mostly Unix network.

---

### Post by bjhutto on 2017-01-16
Thank you for the reply! I am very much an amateur when it comes to Linux.

using ls -l, the drive and 'share' folder both show the same thing

drwxrwxrwx 1 USER GROUP 4096  

'user' and 'group' are both me/mine, so to speak; neither ownership is set to plex, but if the plex user is a member of 'my' group, then shouldn't it have access? I've checked, and 'plex' is definitely set as a member of my group.

The drive itself (2tb, fwiw) is formatted NTFS. That's because this project started out converting a dvd collection to digital media on my Windows machine. And that's why I want a Samba share, so that I can continue to convert dvds (and CDs, etc) to digital on my Windows computer and then move them over the network to my Linux HTPC, which is running the Plex server for the household.

(As an aside, one of my next goals is to set up a bittorrent sync relationship between my music folder on my Windows computer and my music folder--also in this 'share' folder--on my Linux htpc so that when I rip or download music to my main computer it's automatically copied to the machine running my plex server. Will that foul things up down the road?)

I'm not willing to re-rip my dvd collection, but if I need to move the files to another drive, reformat this one, and then move them back, I'm willing to do that. I have another drive that's 1.5tb and that's formatted ext4, so it's big enough, but I'm concerned that my machine isn't powerful enough to move 1tb-plus of files back and forth without something going wrong. The machine is an ECS Liva X ([http://www.anandtech.com/show/8883/ecs-liva-x-review-a-fanless-bay-trailm-minipc](http://www.anandtech.com/show/8883/ecs-liva-x-review-a-fanless-bay-trailm-minipc)). Would you trust it?

Again, thanks so much for your help!

---

### Post by TheFu on 2017-01-16
If the drive is inside a Linux system, it really should be formatted with a Linux file system, like ext4.  This make dealing with permissions easier for both Linux and Samba needs.  

I can't help with NTFS and samba, just have seen issues with it here that were more complicated to solve and often weren't possible to solve easily. NTFS permissions are generally set at mount time, though I understand with some extra work, true POSIX permissions are possible.  Don't use NTFS much here on Linux and generally prefer it on portable drives. If Windows needs access, they can get it off a Linux machine over the network.

Can't comment on specific HW. I only know what I know and nothing else. I've been burned by specialty mini-PCs - heating issues and lack of expansion, plus they are usually $150+ too expensive for what they provide, IMHO.  A half-case computer (if size is a concern) that is fairly powerful can be had for $450. If you want more storage, use a larger case + external arrays. If noise is an issue, put the storage/server device in the basement and have silent playback devices. There are lots of $40-$70 solutions for that.

My simple advice around HW are these small things that I've learned the hard way:
a) Never buy seagate-anything (since around 2007). Generally use Hitachi for the most problem-free storage. Enterprise storage is different.
b) Always use Intel PRO/1000 NICs or Intel NICs that use the e1000 driver. Avoid Realtek.
c) Use the Intel iGPU unless there is a very specific need for something else. 
d) Get a cheap laser jet for printing that has kernel support. Avoid ink-based printers. Kernel supported HW makes life easier.
e) Home users should use flexible Linux SW-RAID, but only after versioned, backups are 100% working. Backups solve 1000 problems. HW-RAID solves 2. Sometimes the fix for RAID issues is a backup. NEVER use fake-RAID.
f) Backups are needed for anything you care about. Run the numbers for the effort spent on the DVD ripping. A backup HDD is cheap in comparison to the effort expended.

Rather than bittorrent, why not use rsync - schedule it to run a few times daily.  I always "pull" from Windows, since the Windows scheduler is about 50x heavier than cron.  Well, actually, I don't keep any data on Windows. For portable devices, using Nextcloud and swap music in/out that I'd like to have on portable devices. NC is only available on the LAN or via a VPN due to security considerations, but can easily setup a tunnel from anywhere in the world to listen to any music in the collection. With sufficient speed, DVD quality videos can be streamed too (no plex account used/needed).

Moving files around should be a NIC and network issue, not related to the CPU much on a LAN. If you have a wired GigE network, this is trivial. Wifi should always be the last resort for many, many, many reasons. Even a 100base-tx network blows away all but the best wifi networks (which require line of sight to come close).  For example, my chromebook has a USB3 port with a USB3-to-GigE adapter.  Gets 920Mbps connections to any of the other systems on the network.  Wifi performance is usually 65Mbps, best-case, on an N-450Mbps network.  Can't really even compare the speed differences when dealing with hidef video files. A GigE LAN is maybe 2% more than a 100base-tx network these days. In a house, it is the difference between $10 and $25 NICs and $10 and $20 GigE switching.  Carefully selected laptops provide gige built-in.  Wifi is a fallback, not a solution.  BTW, I've designed wifi deployments for about 1200 locations, so I know the limits of the tech.

So - looked up that system. Definitely not good for a plex server. Not enough CPU to transcode anything, which is sorta the reason for Plex over the other, F/LOSS, options. [https://www.cpubenchmark.net/cpu.php?cpu=Intel+Celeron+N2808+%40+1.58GHz](https://www.cpubenchmark.net/cpu.php?cpu=Intel+Celeron+N2808+%40+1.58GHz) only 950 passmarks. Have a 3 yr old chromebook here that gets 1500 passmarks - used that would cost about 50% less.

Or get a $50 G3258 CPU and $50 motherboard, shove those into an old case, reuse some old DDR3 RAM, old disks, and you'll have a system that can easily support plex, calibre, NFS, samba, and run a desktop nicely for about $150.  About 3950 passmarks.  Plus I bet that Celeron costs more for 4x less performance!

If you want to search a little more for lots and lots of power, but still on a budget, get something with a used Xeon E5-2660 or 2670 CPU. Those are about $70-90 these days and provide 11K passmarks each. Intel CPUs basically NEVER go bad regardless of what they've been through. The hard part is finding a compatible motherboard for less than $400 that fits into a normal case. That has eluded me. ;(

You already know this, media center playback device doesn't need local media or much CPU - it just needs HW support for video decoding - a Raspberry Pi v2 or v3 can easily do that for about $55 (that gets you everything needed), silently.

Hopefully, you don't think too much of this is off-topic.

---

### Post by TheFu on 2017-01-16
oh, and if the group shows up at "plex" after the NTFS is mounted, then it should work. Plex only needs read access to media. Write is only needed if you want clients to be able to delete the media files.

Clients like Plex or Kodi or Kodi+PlexBMC work best with NFS, not CIFS, access.  NFS is faster and the native file sharing protocol for Unix systems. Alas, I don't think it works with NTFS as the storage - definitely not well - if it works at all.

---

