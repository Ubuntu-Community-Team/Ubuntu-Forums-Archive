---
title: "Adapting  to a windows network"
date: 2008-06-21
forum: New to Ubuntu
---

### Post by beachdrug on 2008-06-21
I have a small business peer lan network which I have several clients which log into a xp file server. I dont use logins as I want open access for all of my staff. 
I would like to use ubuntu as the file server and help prevent some of the window style crashs on the server whenit is left running too long without a reboot.
I managed to work on a computer which I have installed 7.10 and installed samba. I managed to get another XP to login to the ubuntu and it seem to run well.

How do I let two clients on the LAN that don't have a password/logins into the samba/ubuntu server without asking to login. I want computer illiterate staff to just turn on their workstation "till1" and have an automatic login to "ubuntu" fileserver. (I set up a maped drive in Windows)

Thanks in advance.
Beachdrug
PS. If successfull I will run all the workstations this way. In the unbuntu I have installed Win4Lin with 2000 which allowed me to run the server as a workstation as well!

---

### Post by Xerp on 2008-06-21
Just set up Samba for anonymous access.

This guide is old, but the Samba bits still hold true:

[http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_share_public_folders_with_read.2Fwrite_permissions_.28Authentication.3DNo.29](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_share_public_folders_with_read.2Fwrite_permissions_.28Authentication.3DNo.29)

---

### Post by beachdrug on 2008-06-26
Thanks solved problem with a public folder

---

