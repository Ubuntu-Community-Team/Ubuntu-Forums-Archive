---
title: "setting up shared files between 2 linux boxes......"
date: 2008-05-20
forum: New to Ubuntu
---

### Post by techno-mole on 2008-05-20
hello,

ive recently built a system to host all our files on, so its kind of like a communal usb stick :)

we have 3 pc's (4 if you include the communal usb stick) all of which are connected to a 4 port router, ive set up networking between the 2 windows xp machines we have (using samba) but im having some trouble setting up the 2 linux machines we have.

i use ubuntu (8.04) and ive installed the same on the storage machine (the usb stick if you like) but i cant get them to network together, if i switch on one of the windows machines then my box sees the share between the other lniux box an the xp box, but this isnt ideal as i dont want to have to turn on an extra pc to get files of the storage machine.

i have been trying to follow this guide - [http://ubuntuforums.org/showthread.php?t=249889](http://ubuntuforums.org/showthread.php?t=249889)

but im not having much luck (i did try the wiki as well, but got really confused) 

its mainly because i dont understand some of the instructions i guess.
so any help will be appreciated, i didnt think it would be this difficult to set up networking between 2 linux boxes, especially when i set up the networking between the xp machines and the linux boxes in 5 minutes.
cheers

---

### Post by hyper_ch on 2008-05-20
ok, your fileserver, is it linux or XP and does it run all the time?

---

### Post by techno-mole on 2008-05-20
linux, and yes it does run all the time, i have found a solution, i did try the method i posted in the start of the thread, although i didnt have any luck with it.

but then i found this - [http://ubuntuforums.org/showthread.php?t=793308&highlight=networking+linux+boxes](http://ubuntuforums.org/showthread.php?t=793308&highlight=networking+linux+boxes)

which from my point of view was a lot easier and is now running, it may not be the best way, but it gives me the access i need.

cheers for the help though.

PS - the last line of your sig is very clever - There are 10 different kind of people... those who understand binary and those who don't!

---

### Post by hyper_ch on 2008-05-20
well, for sharing between linux clients either use NFS or SSHFS... (main) difference is, that SSHFS is encrypted... so all the data between the machines will be encrypted. You can mount the remote/shared directory at startup or write yourself a small script that you can run to mount it.

I use SSHFS for mounting remote server directories into my file system and I use this script:
```

#!/bin/bash
sshfs web1@REMOTE_SERVER:/var/www/web1 /var/www/web1 -o uid=667 -o gid=667

```
thise will start a connection to REMOTE_SERVER with "web1" as user. Then It mounts the directory /var/www/web1 directory on the server locally as /var/www/web1 (you need to create the folder first where you want to mount anything to). As the user and group id of web1 are not the same as the local my normal user on my machine, I need to adjust that also.
For you it could be something like this:
```

#!/bin/bash
sshfs USER@FILE_SERVER:/home/USER/exchange /home/USER/Desktop/FILESERVER -o uid=1000 -o gid=1000

```
That would mount the /home/USER/exchange folder onto your desktop as FILESERVER. 
In order to get SSHFS working, you first need to install it on your desktop (not on the fileserver) and your fileserver needs to get installed openssh-server.

As said, you can either mount that as start up or make a little shell script that you can just run whenever you need it.

---

