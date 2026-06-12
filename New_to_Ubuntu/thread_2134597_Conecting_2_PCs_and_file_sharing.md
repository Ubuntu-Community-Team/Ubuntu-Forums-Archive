---
title: "Conecting 2 PCs and file sharing"
date: 2013-04-11
forum: New to Ubuntu
---

### Post by GeordieJedi on 2013-04-11
Hi all.

Ok, I'm wanting to share files between my two PCs.
(However, I reckon I've now overthought this. And I'm thinking round in circles).

For example,

I have 2 PCs (1 x desktop 1 x laptop). My laptop has become my main machine however, my
desktop has most of my data on it (music and photos in particular).

I would like to know the best way to connect and transfer files between the two machines
(preferably via a GUI).

E.G. I have new photos on my laptop and I'd like to transfer them to the desktop PC.
But I need to do this visually so that I can compare the two directories and just copy
what I need to across.

1.How do I connect my two PCs and and share my files ?
Can I use my router (downstairs) via wifi to connect both machines together ?

2.How do I transfer my files between my two PCs ?
Samba, SSH, remote desktop ? Ethernet cable ?


Useful Info

2 PCs both running Ubuntu 12.04 + KDE
1 x laptop
1 x desktop

Both PCs are located upstairs (next to each other), and use wifi to connect to the
internet via a (router which is downstairs).

Both PCs are not connected to one another.



Thanks in advance for any help.

---

### Post by TheFu on 2013-04-11
This is what a network is all about.  WiFi sucks, especially when there are lots of files or a few are large ... for certain definitions of "large."
Wired ethernet is always, always, always, always, always, always, always, always, always better than Wifi. Use wired if you can, clear?  A $15 router in the same room would be the easiest to get these system talking and if it is wifi, you could let the router be a bridge into the main wifi router downstairs.  This may be beyond you current skill, but there are lots of how-tos available via google.  Using dd-wrt or tomato should make this easier - these are replacement firmwares for wifi routers.

The "best" answer depends on how much you want to have shared files.  For Linux-to-Linux file connectivity, NFS is the "best" answer. It provides full file permissions and remote files appear to be locally mounted, but I'd never do that over a wifi connection. NFS needs a solid, always-on, always-available connection that wifi simply does not provide.  

The simple and easy way is to use sshfs.  You won't use a GUI to make the connection, but you will be able to see the remote files as though they were local from whatever GUI program you normally use.  sshfs has overhead that NFS doesn't, so the performance will be noticeably worse. On a fast network, that doesn't matter. Further, sshfs doesn't support all the normal file system capabilities like softlinks and hardlinks, but I get the feeling you don't use those at all.  sshfs will also work over wifi - it is more tolerant to bad connections.

I would avoid using samba or cifs for this.  While it can work, the lack of permissions control and simply using a foreign protocol between 2 Linux systems feels "wrong."  Remote desktops would be fine for access the files, but graphics performance is poor - forget about streaming videos.  I have a gigE wired network and just flipping through photos is a pain over a remote desktop. I couldn't imaging doing that over wifi.

---

### Post by Hadaka on 2013-04-11
Hi, you could also do it the no software,no cables
no ssh,no router moving by simply buying a $10
32gig usb stick,make a folder for the music you want
to transfer and a folder for the files. Then simply drag
and drop them from the desktop computer to the usb stick.
then of course drag them off the stick onto the laptop.
in the end ..its quick,simple and inexpensive..and the bonus 
is...you now have a backup of those files on a usb stick.

---

### Post by TheFu on 2013-04-11
You could also directly connect the 2 PCs via ethernet with a crossover cable, but one of the machines should be smart enough to toggle the pins in software so that any ethernet cable could work.  Then it would just be a matter of manually setting up the networking correctly on each ... to be on a different subnet than the main wifi network and provide a higher "metric" between those two machine than the default route/wifi network.  
Google found this: [http://nixcraft.com/linux-software/888-how-connect-two-linux-installed-system-using-ethernet.html](http://nixcraft.com/linux-software/888-how-connect-two-linux-installed-system-using-ethernet.html)
and
[http://superuser.com/questions/279543/connecting-two-linux-pcs-via-cross-cable](http://superuser.com/questions/279543/connecting-two-linux-pcs-via-cross-cable)

Then you could setup NFS on the "server" - which ever machine has more storage. You could cross-mount, if you like, but I'd make certain that the mount points were identical on both machines AND be certain that userIDs match exactly on both systems.  For just 2 system, manually doing this is easy enough, but in a corporate environment, NIS+ or using the LDAP-pam authentication module would be advised to avoid uid collisions which could provide file ownership to an account that doesn't actually own the files.

The USB flash drive isn't a bad idea, but if you have a few TB of data, that will never work.

---

