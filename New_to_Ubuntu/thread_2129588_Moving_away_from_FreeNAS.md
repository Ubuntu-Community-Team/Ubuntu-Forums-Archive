---
title: "Moving away from FreeNAS"
date: 2013-03-26
forum: New to Ubuntu
---

### Post by creepwood on 2013-03-26
First time poster and a novice linux user. I've been using a unbutu desktop 12.10 installation on my secondary desktop for a couple of months now so I'm still fairly new to this.

I have had a FreeNAS server running for a couple of years now and have decided to move away from this platform for sharing data over my LAN. My motherboard on the NAS broke down and I'm contemplating if I should get a new one or just leave it at that.

What I wonder is. What kind of software is there to share data over the network in a secure way. I used ZFS as file system on my NAS since I felt that a software based redundancy was the way to go so I won't get stuck in a specific hardware trap if something would fail. Also the built in bit rot check I liked but isn't ultimately necessary to continue. I'm considering moving over to mirroring drives instead of a 4-drive raidz (raid 5 equivalent). What I also liked was the pooling of vdevs so that they appeared as one big drive with shares on them. Would that be possible to atleast simulate? ATM I'm not reliant on a media server setup. just sharing through CIFS (Windows user and XBMC user). I wouldn't mind using ZFS on linux if it's stable.


The properties of files is a bit of a concern, I tried to copy png files to my a cifs share on my linux machine from my windows 7 machine and got a message that not all file properties would go along with the file. I have no idea what ramification that will bring in the end.

Please be nice. :)

---

