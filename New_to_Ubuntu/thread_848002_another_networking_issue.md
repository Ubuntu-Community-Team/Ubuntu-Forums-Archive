---
title: "another networking issue"
date: 2008-07-03
forum: New to Ubuntu
---

### Post by techno-mole on 2008-07-03
hello again.

im still trying to figure out the cause of this issue.
basically i have 4 pc's on a router, 2 run xp and 2 run ubuntu, ive set up networking and all is well between to 2 linux systems, but for some reason the xp machines wont allow write access to their respective shared folders.

however the xp systems have full access to the shared folders on the linux systems, eg - you can create / delete move files about etc from the xp machines, but you cant do anything to the xp shared folders from the linux systems.

this never used to be a problem, in fact it was (imo) easier to set up networking under ubuntu than it was under xp, i have changed the permissions of the xp shared folders, but they still wont allow full access (write as well as read) even though they say they do.

i dont think this is a samba issue, but more an issue with xp, before all i needed to do was setup the shared folders on the linux systems and then run the network setup wizard on the xp systems and that was it, i didnt need to mess about changing permissions on the xp systems or anything else.
so at the moment im stuck because i have network folders that i cant do anything with, so im looking for an easy way to allow the xp shared folders to be written to from the linux systems, and to be honest i dont see why it shouldnt be simple.
any takers ?

---

### Post by iaculallad on 2008-07-03
Try to see the solution/suggestion I posted on this [thread]("http://ubuntuforums.org/showthread.php?t=847837"). It uses smbfs.

---

### Post by techno-mole on 2008-07-03
maybe thats the problem ? im not sure the router im using assigns static ip's, but then it never used to be a problem.
cheers ill give it ago.

---

### Post by iaculallad on 2008-07-03
> **techno-mole said:**
> maybe thats the problem ? im not sure the router im using assigns static ip's, but then it never used to be a problem.
cheers ill give it ago.

You are to assign static IP's, your router (if configured) assigns dynamic IP's.

---

### Post by techno-mole on 2008-07-03
cheers for the help, i have tried the steps that you linked to, but i still dont have write access to the shared folder on the xp system.

---

### Post by benfindlay on 2008-07-03
Have you set up permissions in the Security tab as well as the Sharing tab in windows?

---

### Post by techno-mole on 2008-07-03
yes, ive adjusted the required sections under security on the windows box, which i never had to do in the past.

---

