---
title: "Unable to view shared folder on virtual box"
date: 2011-10-22
forum: New to Ubuntu
---

### Post by hoangtu69 on 2011-10-22
I have Windows 7 as host and Ubuntu 11.10 as Guest running on VirtualBox 4.1.4.  Below are the steps
 
1) Installed Guest Additions
2) Created a permanent share folder (R/W), auto mount  and point it to my Downloads folder on Win7 using the GUI interface
3) Restart
4) Browse to it via File System within ubuntu to /media/sf_Downloads but I got the below error message
 
The folder contents could not be displayed
You do not have the permissions neccessary to view the contents of "sf_Downloads"
Do you have any ideas?

---

### Post by masgeeks on 2011-10-22
Interesting, I used to have the reverse problem, ubuntu host and w7 guest, and my w7 guest could not access shared folder on ubuntu.  It always had, but one VB update had blown that up somewhere along the line.  However, after going to 4.1.4 my shared folder issued resolved themselves across the board in all my VM's...

I never could figure out what the problem was...  :(

---

### Post by haqking on 2011-10-22
> **hoangtu69 said:**
> I have Windows 7 as host and Ubuntu 11.10 as Guest running on VirtualBox 4.1.4.  Below are the steps
 
1) Installed Guest Additions
2) Created a permanent share folder (R/W), auto mount  and point it to my Downloads folder on Win7 using the GUI interface
3) Restart
4) Browse to it via File System within ubuntu to /media/sf_Downloads but I got the below error message
 
The folder contents could not be displayed
You do not have the permissions neccessary to view the contents of "sf_Downloads"
Do you have any ideas?

do you have the extensions pack installed ?

---

### Post by WanderingAlbatross on 2011-10-23
Even if you do have it installed you may have to do it again.  I have had to re-install the guest additions after a VB version upgrade.

---

