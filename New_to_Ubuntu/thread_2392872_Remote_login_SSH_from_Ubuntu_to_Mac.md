---
title: "Remote login SSH from Ubuntu to Mac"
date: 2018-05-26
forum: New to Ubuntu
---

### Post by mac187 on 2018-05-26
Hi, dont know where to ask.. And i have been searching all over google .. Maybe im blind but i need to ask here..

I can login to my mac trough ssh from my ubuntu 18.04 , but i want to get files from mac to my ubuntu.. How can i do that? Thanx

---

### Post by TheFu on 2018-05-26
scp, sftp, rsync  - you can push or pull files with any of these.  If you setup ssh-keys between the systems, it will be both more convenient AND more secure.  These are part of the normal ssh system.  Apple probably names them something different to be "user friendly" ... and confusing. 

To remote in from Ubuntu to a Mac, the mac has to be running an ssh-server process. 
After that is setup, just open any terminal on Ubuntu and type **ssh {mac-userid}@{mac-IP}**.   If the userid on the mac is the same as on ubuntu, you can leave that part off.  Replace the mac-IP with the correct IP (or DNS name if you've set that up).  So, in my home, if I had a mac (192.168.5.32) with the same userid as I use on Ubuntu, I'd type **ssh 192.168.5.32** to get a remote shell.  If I want to use sftp, then I'd type **sftp 192.168.5.32**.  sftp uses the same commands as plain FTP, just through an ssh session.  Only the commands are similar, it is NOT the same underlying protocol.

If OSX is running the openssh-server, then you can use almost any file manager on Linux to access the Mac with a URL like sftp://mac-ip/  ... then you should be prompted for login credentials (assuming you didn't setup ssh-keys). If you do setup ssh-keys, the connection will appear automatic.

From Windows, WinSCP is the tool to connect via sftp to Linux openssh-servers.

I have no idea what GUI programs a Mac might have. Filezilla, perhaps?  You'd have to google or what for someone else.

Have you tried these already?  I bet there are 50 youtube videos about setting up and using openssh-server on a mac.

There are 100+ other ways, depending on what you are able to setup and what you want to work.  You can use NFS, CIFS, sshfs, NextCloud, OwnCloud, seafile, and those are off the top of my head.  Each has pros and cons.  

Hopefully, I've covered enough different ways that 1 will work for you.

---

### Post by mac187 on 2018-05-27
Thank mate !

---

