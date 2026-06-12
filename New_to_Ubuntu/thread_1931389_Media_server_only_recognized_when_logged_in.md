---
title: "Media server only recognized when logged in"
date: 2012-02-25
forum: New to Ubuntu
---

### Post by glenak1911 on 2012-02-25
Hi guys I turned an old desktop into a media server running Ubuntu server 11 and I have Samba and Mediatomb running to serve my media. Samba allows me to map a drive on my laptop and Mediatomb allows me to stream to my playstation.

My problem is that this week I've only been able to access files, and folders when I'm logged into the server via Putty. When I close my putty session, windows stops recognizing the mapped drive, and the icon for Mediatomb on my ps3 disappears. 

I was wondering if anybody has had this issue before or if they knew how to go about troubleshooting it?

---

### Post by AgentZ86 on 2012-02-25
> **glenak1911 said:**
> Hi guys I turned an old desktop into a media server running Ubuntu server 11 and I have Samba and Mediatomb running to serve my media. Samba allows me to map a drive on my laptop and Mediatomb allows me to stream to my playstation.

My problem is that this week I've only been able to access files, and folders when I'm logged into the server via Putty. When I close my putty session, windows stops recognizing the mapped drive, and the icon for Mediatomb on my ps3 disappears. 

I was wondering if anybody has had this issue before or if they knew how to go about troubleshooting it?

I'm assuming your server has user groups setup so you can identify which users and group have access to the shared resource ?

Then those users must login as the same workgroup for an available shared resource that is available to that user/group

If no permission is given to access the server then it may not allow access to those files / folders

It sounds like you logged in via putty from the windows box and had permission and while permission for the mapped drive was granted, the PS3 was able to access the shared resource of the windows mapped drive so long at it was logged in as root

So you need to give read/write access to the user/group and those computers that want to access those resources must have the same group priviledges.

I don't know how you set it up before but typically the credentials are checked to be sure there is permission for this.

However, how do you setup your server on the local network providing DHCP to the rest of the network or is the server acting as a shared client inside the local network and getting it's IP from the router ?

You don't want to have 2 DHCP servers trying to give IP's to the local network and subsequently giving out different IP's and group names within the same IP range etc.

Anyhow not sure if this helps or creates more confusion but there is a bunch of things that could cause this.

Post more info if you got it.

---

### Post by glenak1911 on 2012-02-26
I'm not sure how to figure out if my server is providing DCHP or if it's acting as a shared client, if you could explain that a bit more...

However, I have assigned it a static IP address, after restarting it and getting different IPs every time. 

I also changed the permissions on my shared folders to a 777 permission, and I'm able to access everything from my computer and my playstation, but I'm not sure how secure that is.

---

