---
title: "Automount + sharing partitions."
date: 2013-03-08
forum: New to Ubuntu
---

### Post by littlegreen on 2013-03-08
Hey guys! 
A total newbie here....

Well - to start off with a laugh - I FINALLY have had enough Windows re-installs. I have this "FileServer" computer at work, storing a lot of data. I have Ubuntu 12.10 desktop x86 installed on it.

What I'd like to achieve (or more ask if it'll work) is this:

I've read a couple of threads about auto-mounting ntfs partitions upon startup. I think I'll handle that easily enough, but I'm concerned about sharing those partitions over the internal network. 

Well, basicly I'm just wondering if I share the /media/ntfs-partition-x folder using samba with all permissions included (Guest access included) - will they be shared, should a power loss ever occur?(After reboot I mean)
(That is assuming they do auto mount upon startup)

And one more thing: what would happen if I mount a different hard drive in the place of another one (just for argument sake)

Cheers!

---

### Post by vanadium on 2013-03-08
If a power loss occurs, they will not anymore be shared. When the server reboots, the drives will again be shared.

---

