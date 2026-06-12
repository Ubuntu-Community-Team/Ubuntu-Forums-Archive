---
title: "VPN, Samba share issue"
date: 2012-10-19
forum: New to Ubuntu
---

### Post by CrouxL on 2012-10-19
I am running Ubuntu Server 64bit, 12.04.
I am connecting to a Microsoft Server 2008, with PPTP VPN, via and ADSL Router over the internet.
My tunnel is up, I can ping the MS server/ip fine.
I created Samba mount points and created the samba shares.
Connecting to the share, using windows, before mounting, allows me to create, read and write just fine.
After mounting the MS share to my mount point using CIFS, I can access the folders and files from within Ubuntu just fine.
(sudo mount -t cifs //ip/share /mnt/share -o username=user,password=userpassword)

The Problem!
From any windows client pc's, connecting to the samba share, all folders are marked as files with 0 size.
The documents in the root of the share can be edited. But the subfolders cannot be accessed at all.
Please help, I have been banging my head for 3 weeks now, and searching the internet for a solution. But I am in need of people with more knowledge than I. 

Thanks

---

### Post by aromo on 2012-10-19
> **CrouxL said:**
> Connecting to the share, using windows, before mounting, allows me to create, read and write just fine.
After mounting the MS share to my mount point using CIFS, I can access the folders and files from within Ubuntu just fine.
(sudo mount -t cifs //ip/share /mnt/share -o username=user,password=userpassword)


You lost me here.  You are connecting to your Linux server Samba share using your Windows clients?

If so, why would you need to issue the mount command on your Linux server?

Are your Windows Clients on the VPN or local to your Linux server?  If local, the VPN portion is irrelevant to the problem.

---

### Post by CrouxL on 2012-10-19
Ok I have a Samba Server in one location (1), with windows clients connecting to it.
Then at another location(2), 1000km's away) is an Microsoft Server 2008.
The MS Server(2) has shares on it that the clients at
(1) needs to have access to, via Ubuntu Server. 
My Ubuntu Server(1) connects to MS Server(2) using VPN.
I then mount the shares(2) on my ubuntu server.
using samba to share the mounted folders for the local clients. (not sure if this is the right procedure)

MS Server ---internet--- Ubuntu VPN, Samba --- windows clients.
(Linux configure point to point tunneling PPTP VPN client for Microsoft PPTP vpn server)

I'll be back on monday, if you still don't fully understand, my head is spinning...

What will be the better solution?, instead of letting each windows client pc connect to MS Server(2) with its own VPN.
I want Ubuntu(1) to connect with the VPN, and have the windows clients have full access to the shared MS Server(2) folders.

Thanks for reply.

---

### Post by aromo on 2012-10-19
Instead of mounting the remote share, why don't you enable routing on your Linux server?

MS Server <--- vpn (PPTP)---> Linux server <--- LAN ---> MS Clients

1. On your Linux server establish a route to the MS server through the VPN interface
2. On your Windows clients establish a route to the MS server through the Linux server

Each user would be able to mount the share from the MS Server without having to establish a VPN each.

My 2 cents.

---

### Post by CrouxL on 2012-10-23
Thanks you very much Aroma

I will look into that...
I have looked into routing on ubuntu server, but it still confuses me.

I have 1 network card (eth0) and that connects to both the internet, and vpn tunnel to my 2nd location.(ppp0)
Server ip is 10.0.1.3. gateway, ip 10.0.1.254, vpn ip 10.0.0.18. The MS server vpn ip 10.0.0.24, MS server ip 10.0.0.2

I have been playing with ubuntu for some time. What I know is but a drop in the bucket!, enough to cause damadge.... :)
Ok, since I suck at this, can anyone provide an example or 2. (stepping stones for me)

Regards


Have taken a look at this link...
[http://ubuntuforums.org/showthread.php?t=2032302&highlight=routing](http://ubuntuforums.org/showthread.php?t=2032302&highlight=routing)

---

