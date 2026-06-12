---
title: "Backing up to Box.Com with Deja Dup Backup"
date: 2013-03-14
forum: New to Ubuntu
---

### Post by n411303 on 2013-03-14
I thought I should share my solution to a secure daily back up to the cloud.  Presently, Ubuntu's default back up programme Déjà Dup Backup will not run a daily automated back up to Ubuntu One.  It will run manually but there is at present a bug with some garbage about "network" see [https://bugs.launchpad.net/ubuntu/+source/deja-dup/+bug/982316](https://bugs.launchpad.net/ubuntu/+source/deja-dup/+bug/982316) 

I recently stumbled on a free 15G offer for box.com and wanted to see if I could use it with Déjà Dup Backup.  The answer is yes and it is working really well: automatic daily to a fully PGP encrypted back up.  

I followed the guidance given here: [http://askubuntu.com/questions/125725/backing-up-to-box-net-account-webdav-and-deja](http://askubuntu.com/questions/125725/backing-up-to-box-net-account-webdav-and-deja)

to install davfs2 and create a secrets file.  In the link, substitute "box.com" for "box.net" which is either wrong or changed.  

I had to tweak the FSTAB instructions they give because of permissions.  After trial and error, I got this entry to automatic mount at boot and work fine:

[https://www.box.com/dav](https://www.box.com/dav) /home/[NAME]/box.com davfs rw,user,uid=[NAME],gid=[NAME],_netdev 0 0

Use: sudo gedit  /etc/fstab and add the equivalent line to your fstab using your name and the path to your box.com mount point.  

In Déjà Dup Backup just set the back up folder to be a suitable "local" folder in the now mounted cloud storage folder.  It looks local but its in the cloud!

Hope this works for you as well as it is working for me.

---

### Post by Cerveth on 2013-03-31
Thanks for the tutorial. Just one question...
I want to make some symbolic links for my new /home/Box folder but every time I try to make the link I got this message:
[I]ln -s ~/Documents ~/Box
ln: failed to create symbolic link «/home/*****/Box/Documents»: operation not supported[/I]
Any suggestions for this problem??? Thanks.

---

