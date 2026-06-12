---
title: "Vista-Ubuntu Connect"
date: 2008-10-17
forum: New to Ubuntu
---

### Post by DeeXener on 2008-10-17
Okay here is a simple breakdown of what I want to do with what I have:

-Computer with Windows XP (won't boot but can load with Ubuntu Live CD)
-Using Ubuntu Live CD 7.10 I believe
-Using another PC with Vista Home Premium

So, I want to retrieve files from the broken XP machine and transfer them from that to my new machine with Vista. But I have to use a Ubuntu live CD to access the other PC. 

What I want to know is how I can get them to talk to each other and be able to send my files from a Ubuntu Live CD machine to the Vista machine.

---

### Post by JasenGroves on 2008-10-17
Why not do it the old fashioned way and drop the XP machine's hard drive into the Vista machine as a slave drive and then just copy the files you need. I've done that more times than I can count. Actually. my work pc still has an old hard disk hooked up as a slave drive currently because I was too lazy to take it out...

---

### Post by crazyness003 on 2008-10-17
> **JasenGroves said:**
> Why not do it the old fashioned way...

Hes got a point. 

But other than that, have you enabled a folder or drive as shared on your vista machine?
Basically you gotta create a workgroup on the vista machine.
Then see open nautilus and click the network icon in the folder tree. 
You should be able to see your vista hosted shared directory or drive under "windows Network" -> "your_workgroup_name" (mine is WORKGROUP) -> "your_vista_machine_name" (mine is Main-PC ... but not vista) -> "your_shared_folder's_name".
Find your files in the xp partition and just drag and drop into the vista folder.

That _*should*_ work. Let us know what happens

---

### Post by eternalnewbee on 2008-10-17
> **crazyness003 said:**
> Hes got a point. 

But other than that, have you enabled a folder or drive as shared on your vista machine?
Basically you gotta create a workgroup on the vista machine.
Then see open nautilus and click the network icon in the folder tree. You should be able to see your vista hosted shared directory or drive. 
Find your files in the xp partition and just drag and drop into the vista folder.

That _*should*_ work. Let us know what happens

Agree. (from experience in the Dark Ages, when I used w#ndows...)

---

### Post by nhasian on 2008-10-17
i have to agree with JasenGroves.  yanking the drive out of the machine and plugging it into the other pc is probably the easiest solution.  however, what you suggest can be done as well assuming you have a bit of knowledge in networking.

both the windows vista and ubuntu pc must be connected to the same network either with a hub/router or directly to each other with a crossover cable.  share a folder on the vista pc (read & write access) and then you should be able to just drag'n'drop the files from one pc to the other.

---

### Post by DeeXener on 2008-10-17
I'll try again. I do have a shared folder on my Vista machine. I would yank the drive out and put it into the other machine but sadly there aren't any drive bays open. My pc is pretty compact so I wouldn't be able to just lay the drive on the floor while I transferred them.

So I have WORKGROUP, my folder for sharing with all settings set (Backup_Network is the name) and my PC's name. I'll try and let you guys know what happens.

Thanks for all the replies.

---

### Post by hovzio on 2008-10-18
Fire up your xp machine with a live dvd, plug in an external hardrive, mount your internal drive if not already is, exit and copy over to your vista machine. simplest to use an external hd with a fat32 filesystem. Hope this helps you.


Edit: You could also install an ssh-server while running live cd and use a windows client like putty (for the vista box)and do it over the network. I have not done this but in theory it will work with ssh, sftp, vnc viewer/client. Ubuntu comes with a vnc server.

---

### Post by DeeXener on 2008-10-18
Could I use a Zen Vision W as a external hard drive in Ubuntu?

---

