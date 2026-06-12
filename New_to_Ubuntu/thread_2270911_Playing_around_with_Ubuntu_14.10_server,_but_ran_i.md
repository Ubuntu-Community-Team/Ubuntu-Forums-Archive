---
title: "Playing around with Ubuntu 14.10 server, but ran in to some trouble..."
date: 2015-03-26
forum: New to Ubuntu
---

### Post by jakob5 on 2015-03-26
Hi there!
So i recently started playing around with ubuntu server, but i ran into some stuff along the way which i ddnt quite understand.

1. problem
I have somehow locked my user to the /home/usrname folder. it occured when i tried to limit FTP acces for another user in vftps. I limited all users to home directory in the config file, but the setting seemed to work only on my user (which is the only sudo user), limiting my ftp acces t home folder but the other user was free to roam all folders. i ended up just deleting the ftp server, but the problem had replicated to my torrent client! now i can only set my download folder to /home/usrname, while i want it to go to /data (a folder structure i have made). I have done chmod 777 on the folder, and chown command. any ideas? :S

2. problem
My home folders seem to be limited! i have setup samba share, to make a personal cloud drive but i am "limited" to 46 gb of data in the home folder. Not that this isnt enough, but i would like to know how to controle this limit :)


best ragards :)

---

