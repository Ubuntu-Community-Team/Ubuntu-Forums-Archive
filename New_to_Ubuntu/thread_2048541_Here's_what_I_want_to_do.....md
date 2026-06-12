---
title: "Here's what I want to do...."
date: 2012-08-26
forum: New to Ubuntu
---

### Post by REAPtheWHIRLWIND on 2012-08-26
*I've been grinding the search boxes of too many sites and have exhausted the almighty Google. PERHAPS the keywords I use for my search have been the problem...*

**_My Setup_:**
**Ubuntu 11.10** (32bit)
**LAN**: 2x Routers..1 main router which leads (via Cat5) to second router, which connects to my computer (via Cat5).
+ other networked devices like a PS3 and Escient SE-D1 (no HDD)
The PS3 and SE-D1 are sharing the same router as my computer.

**_My Goal_:**
I would like to have files on my computer become accessible by somehow making my computer into a **local server** for those devices; granting local access to stream media over the network to these devices.

**_What I've Tried_**:
> In my search, I followed instructions for setting up *MySql*, *Apache2*, *Samba*, and *Lamp-server*.

What I've gathered from my testing, they were showing me how to make virtual hosts... I'm not entirely sure this is what I need to do, with the exception of the SE-D1. (*It requires an http:// host to play media from a remote server.*)

Can any of you ladies and jelly spoons point me in the right direction on this - or provide the correct terminology for future searches on this topic?

Thanks.

---

### Post by linuxguy049 on 2012-08-26
> **REAPtheWHIRLWIND said:**
> *I've been grinding the search boxes of too many sites and have exhausted the almighty Google. PERHAPS the keywords I use for my search have been the problem...*

**_My Setup_:**
**Ubuntu 11.10** (32bit)
**LAN**: 2x Routers..1 main router which leads (via Cat5) to second router, which connects to my computer (via Cat5).
+ other networked devices like a PS3 and Escient SE-D1 (no HDD)
The PS3 and SE-D1 are sharing the same router as my computer.

**_My Goal_:**
I would like to have files on my computer become accessible by somehow making my computer into a **local server** for those devices; granting local access to stream media over the network to these devices.

**_What I've Tried_**:
> In my search, I followed instructions for setting up *MySql*, *Apache2*, *Samba*, and *Lamp-server*.

What I've gathered from my testing, they were showing me how to make virtual hosts... I'm not entirely sure this is what I need to do, with the exception of the SE-D1. (*It requires an http:// host to play media from a remote server.*)

Can any of you ladies and jelly spoons point me in the right direction on this - or provide the correct terminology for future searches on this topic?

Thanks.


Why not just make shared folders with media in them? Is this not possible on Linux?

I mean, I've got essentially the same setup (minus having 2 routers [WHY?!], I've got 1 router, 1 switch), on a Windows 7 Home PC, which shares the files. My xbox connects to it via ethernet, and my families' PCs all connect to it via wifi.

Maybe I'm just not understanding the situation properly, but I don't see the need for Apache (which I'm pretty sure is used exclusively for web stuff), mySQL (I don't think you want databases of media)... YOLO, SO SHARE!


EDIT: I had originally said my ps3 connects to my pc as a shared media centre, but I lied. It's my xbox. lol

Still though, I'm not quite sure a SQL or Apache server is what you want for media files.

---

### Post by Gone fishing on 2012-08-26
The only thing you need to do is setup Samba and Samba users if you are sharing with Windows boxes or NFS if Linux boxes, in fact you could just use NFS as Windows 7 can mount NFS shares 

[http://answers.microsoft.com/en-us/windows/forum/windows_7-windows_programs/nfs-client-for-windows-7/42aae25d-d077-4ff9-abdf-7314a589c46d](http://answers.microsoft.com/en-us/windows/forum/windows_7-windows_programs/nfs-client-for-windows-7/42aae25d-d077-4ff9-abdf-7314a589c46d)

and here's a link to an NFS howto

[https://help.ubuntu.com/community/SettingUpNFSHowTo](https://help.ubuntu.com/community/SettingUpNFSHowTo)

---

### Post by Miljet on 2012-08-26
+ 1 for NFS. Here is a link to another guide to setting up NFS.

[http://mostlylinux.wordpress.com/network/nfshowto/](http://mostlylinux.wordpress.com/network/nfshowto/)

---

