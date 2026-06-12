---
title: "Home wireless network using ubuntu, how?"
date: 2008-11-29
forum: New to Ubuntu
---

### Post by gychang on 2008-11-29
Laptop downstairs running 8.1 on wireless card, one upstairs main computer with router attached running the 8.1.

I want to be able to exchange files between the 2 computers, can someone let me know each step?

thanks in advance.

gychang

---

### Post by starcannon on 2008-11-29
Samba is the most common way to do this; I will link you some guides, and of course if you get stuck on something be sure to ask again in this thread.
[https://help.ubuntu.com/community/SettingUpSamba](https://help.ubuntu.com/community/SettingUpSamba)
[http://www.howtogeek.com/howto/ubuntu/install-samba-server-on-ubuntu/](http://www.howtogeek.com/howto/ubuntu/install-samba-server-on-ubuntu/)
[http://www.ubuntu-unleashed.com/2007/08/howto-quickly-easily-setup-samba.html](http://www.ubuntu-unleashed.com/2007/08/howto-quickly-easily-setup-samba.html)
[http://www.watchingthenet.com/enable-file-sharing-in-ubuntu-using-samba.html](http://www.watchingthenet.com/enable-file-sharing-in-ubuntu-using-samba.html)

It can be a little involved your first time through; but once you have the hang of it, its not to bad. Be sure to ask questions here as you go.

GL and Have fun.

---

### Post by lswb on 2008-11-29
If you only have linux machines on your network, the easiest method is to install the package "openssh-server" on both machines and optionally "sshfs"

Then you can simply go to Main Menu/Places/Connect to Server, select SSH as the server type, and in the "Server" field enter the hostname or ip address of the other machine, and hit connect. You'll be prompted for a password and maybe a username for the other machine. After that the other system will be on your places menu.

With the sshfs package, you can use the cli to mount a remote system to a local mountpoint similar to how a disk or partition is mounted, Then you can access it with any file browser or command line tool the same as if it was a locally mounted filesystem.

---

### Post by gychang on 2008-11-29
> **lswb said:**
> If you only have linux machines on your network, the easiest method is to install the package "openssh-server" on both machines and optionally "sshfs"


Thanks, I was able to connect my 2 home ubuntu computers together, great.  Now the next challenge.

I login to my office computer running XP with my home computer running XP but now I want to completely go with ubuntu at home if possible.  My goal is to rid of XP at home all together, office computers are out of my control unfortunately.

I know the IP address of the office windows XP, how do I do this?

thanks in advance.

gychang

---

### Post by starcannon on 2008-11-29
Are you wanting a remote desktop situation? or just to share files with the Windows computer?

If its file sharing from windows to linux to windows, Samba is what your going to need, if your wanting a remote desktop, its already built into your Ubuntu station:
Applications>Internet>Remote Desktop Viewer

You can also use windows to Remote in to your Ubuntu machine, but you'll likely need to install some additional software on windows; such as [TightVNC]("http://www.tightvnc.com/") , and then setup your Ubuntu to accept remote desktop connections:
System>Preferences>Remote Desktop

Both Samba and Remote desktop are fairly simple to setup in Ubuntu, so don't be afraid to give them a go, just be sure to give yourself time to learn and room to make a mistake or 2.

GL and have fun.

P.S. Heres a good step by step guide to Samba (I dug some more :) )
[http://myy.haaga-helia.fi/~a0500231/linux/samba/](http://myy.haaga-helia.fi/~a0500231/linux/samba/)
And heres one using the SWAT gui for Samba:
[https://help.ubuntu.com/community/Swat](https://help.ubuntu.com/community/Swat)

---

### Post by gychang on 2008-11-29
> **starcannon said:**
> Are you wanting a remote desktop situation? or just to share files with the Windows computer?

Its already built into your Ubuntu station:
Applications>Internet>Remote Desktop Viewer

Both Samba and Remote desktop are fairly simple to setup in Ubuntu, so don't be afraid to give them a go, just be sure to give yourself time to learn and room to make a mistake or 2.

GL and have fun.

P.S. Heres a good step by step guide to Samba (I dug some more :) )
[http://myy.haaga-helia.fi/~a0500231/linux/samba/](http://myy.haaga-helia.fi/~a0500231/linux/samba/)
And heres one using the SWAT gui for Samba:
[https://help.ubuntu.com/community/Swat](https://help.ubuntu.com/community/Swat)


thanks for all your help, initially I started to get the home ubuntus together and with your help and others got it going quickly.  Now I am getting bolder and want to remotely connect to my office XP machine.  Looks like what I need is already built in, will have it a go tonight...

gychang

---

### Post by Xiong Chiamiov on 2008-11-29
For networking Linux machines, I find NFS to be easier and more efficient thatn SSHFS, as it's designed specifically for that, rather than being a hack onto SSH. [[guides]("http://delicious.com/xiong.chiamiov/nfs")]

Also, it's actually version 8.10 you're running, rather than 8.1.  Although normally they would indicate the same thing, Ubuntu's version numbering reflects the date of release.  Thus, 8.10 indicates a release in the 10th month of the 2008, so 6 months after 8.04 and 1 year after 7.10.

---

### Post by lswb on 2008-11-29
> **Xiong Chiamiov said:**
> For networking Linux machines, I find NFS to be easier and more efficient than SSHFS, 

Surely you must be joking? :)

---

### Post by Xiong Chiamiov on 2008-11-29
> **lswb said:**
> Surely you must be joking? :)
NFS is ridiculously easy to set up for both client and server.

---

