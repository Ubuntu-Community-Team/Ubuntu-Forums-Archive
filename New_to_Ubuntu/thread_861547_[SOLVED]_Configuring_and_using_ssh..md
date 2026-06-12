---
title: "[SOLVED] Configuring and using ssh."
date: 2008-07-16
forum: New to Ubuntu
---

### Post by fullmetalgerbil on 2008-07-16
I've got two computers running Ubuntu 8.04, both behind the same router, and I've been trying to figure out how to share files and browse folders between them. I posted in the networking section and someone told me to make each computer a NFS server and client-along with a link to some instructions I could not make heads nor tails of. Sombody else suggested ssh and made it seem like all I had to do was run sudo apt-get install sshserver.
Of course, that command didn't work but using a different one allowed me to install an ssh server on each computer.
Now the problem is I dont know what to do to configure and use ssh now that its installed.

---

### Post by EndlessWaltz1026 on 2008-07-16
> **fullmetalgerbil said:**
> I've got two computers running Ubuntu 8.04, both behind the same router, and I've been trying to figure out how to share files and browse folders between them. I posted in the networking section and someone told me to make each computer a NFS server and client-along with a link to some instructions I could not make heads nor tails of. Sombody else suggested ssh and made it seem like all I had to do was run sudo apt-get install sshserver.
Of course, that command didn't work but using a different one allowed me to install an ssh server on each computer.
Now the problem is I dont know what to do to configure and use ssh now that its installed.

I am new to Ubuntu too so don't quote me on this information. I had thought that SSH was for accessing your computer via remote. I may be wrong on that information but here is a link to some information on setup.

[http://www.jonathanmoeller.com/screed/?p=228](http://www.jonathanmoeller.com/screed/?p=228)

Hope this helps.

---

### Post by bodhi.zazen on 2008-07-16
You can use any number of protocols, choose one, follow a walk-through, and ask specific questions if you get stuck.

Options, in my order of preference, would be :

samba, nfs, ssh (sshfs actually), http (apache), and ftp.

Samba : [http://doc.ubuntu.com/ubuntu/serverguide/C/windows-networking.html](http://doc.ubuntu.com/ubuntu/serverguide/C/windows-networking.html)

[uwiki]ComprehensiveSambaGuide[/uwiki]

[uhelp]community/SettingUpSamba[/uhelp]


ssh :

[uwiki]SSHHowto[/uwiki]

[http://ubuntu.wordpress.com/2005/10/28/how-to-mount-a-remote-ssh-filesystem-using-sshfs/](http://ubuntu.wordpress.com/2005/10/28/how-to-mount-a-remote-ssh-filesystem-using-sshfs/)

    [http://ubuntu-tutorials.com/2007/01/02/mount-remote-directories-securely-with-ssh-ubuntu-6061-610/](http://ubuntu-tutorials.com/2007/01/02/mount-remote-directories-securely-with-ssh-ubuntu-6061-610/)

NTP : [http://doc.ubuntu.com/ubuntu/serverguide/C/network-file-system.html](http://doc.ubuntu.com/ubuntu/serverguide/C/network-file-system.html)

FTP: [http://doc.ubuntu.com/ubuntu/serverguide/C/ftp-server.html](http://doc.ubuntu.com/ubuntu/serverguide/C/ftp-server.html)

http : [http://doc.ubuntu.com/ubuntu/serverguide/C/httpd.html](http://doc.ubuntu.com/ubuntu/serverguide/C/httpd.html)

---

### Post by fullmetalgerbil on 2008-07-16
this probably sounds really dumb, but I noticed on the Samba info it talks about sharing between a Linux computer and a Windows computer. Of course this will work between two Linux computers, right?

---

### Post by bodhi.zazen on 2008-07-16
Yes samba works between two linux computers. Only 1 needs to be a server.

Samba is as easy as any other (server) to set up and it is a little more secure then nfs.

ssh is a little over kill for your situation. ssh is used primarily for remote access and uses encryption for data transfer. Thus, IMO, better for connections over the internet. You are behind a router and do not need shell access, so samba is better.

ftp and http are both easy. Similar issues here. ftp is less secure, but you are OK behind a router. Both ftp and http are network (internet) protocols and a little overkill.

---

### Post by fullmetalgerbil on 2008-07-16
Ok, thanks. I'll give Samba a try, only I'm nervous about editing the config files. That was the part which was flummoxing me when I tried NFS and ssh.

---

### Post by fullmetalgerbil on 2008-07-16
Also, if only one computer needs to be set up as a server then do I still have to instal Samba on both computers?

---

### Post by bab1 on 2008-07-16
I would always defer to bodhi.zazen as he has more Ubuntu experience.  But I think for clarity it should be said that Samba is for the SMB/CIFS (server message block ie: Windows) file systems.  It is easy to learn but you are crossing from ext2/3 to CIFS and back for no reason.  NFS is the file sharing system for linux (UNIX types).  Properly installed you will not even know what is on one host and what is on another.  The other ideas mentioned above are for "terminal sessions" or file transfer.

---

### Post by bodhi.zazen on 2008-07-16
Thanks bab1, I used to think that too. Samba is, in a nutshell, the opensource version of a Microsoft Network protocol. You can use samba independent of the file system on the hard drive. Samba uses permissions, although they are set a little different is all.

I was a big fan of NFS before, but samba is, IMO, more secure. NFS is akin to ftp that way.

You *might* be interested in this link :

[http://www.samba.org/samba/docs/SambaIntro.html](http://www.samba.org/samba/docs/SambaIntro.html)

---

### Post by fullmetalgerbil on 2008-07-16
I'm sitting here with Samba installed on one computer, having no idea whatsoever with what to do next as far as configuring whatever-the Comprehensive Samba Guide makes no sense to me since near all the commands are for windows machines, and I still dont know if Samba needs to be installed on both machines nor what to do if I do install it on both.
By the way, this day four and thread number two of trying to figure out how to simply share files between two Ubuntu computers. I used to love the challenge and learning curve involved with running a Linux box, but right now its a royal pain in the butt.

---

### Post by bodhi.zazen on 2008-07-16
LOL

Samba is as easy to configure as windows.

By default the client software is installed with Ubuntu.

All you need to do is follow the sections in the gui tools.

On the server, go to "Places -> home"

Right click on any directory (folder) DO NOT SHARE YOUR HOME DIRECTORY.

from the menu select "sharing options" -> install samba from the next set of pop up menus.

Log out and back in.

Re-select a directory to share, right click -> share options. Select rw or ro share, give the share a name.

On your other computer, the client, go to 

Places -> Network -> browse to the server -> click on the share -> enter user name and password you would use to log into the server -> done.

It is no different then Windows.

---

### Post by fullmetalgerbil on 2008-07-16
Thank you so much bodhi.zazen, this is exactly what I needed. I followed the instructions and it totally worked. Actually, its even easier than Windoz. I cant believe I let it frustrate me so much:lolflag:

---

### Post by bodhi.zazen on 2008-07-17
> **fullmetalgerbil said:**
> Thank you so much bodhi.zazen, this is exactly what I needed. I followed the instructions and it totally worked. Actually, its even easier than Windoz. I cant believe I let it frustrate me so much:lolflag:
You are most welcome, glad all is well. There are a lot of threads on samba, but once it clicks most users feel it is fairly easy :twisted:

Welcome to Ubuntu, hope you stay.

---

### Post by Anthony M on 2008-07-17
I am having a similar problem where I can right click and share files, but cannot view them over my network of two Ubuntu computers.  When i open "Network" all I see in "Windows Network".

---

### Post by cariboo on 2008-07-17
THat's normal when using samba. Double click the windows network icon and you should see your workgroup, double click the workgroup icon and you should see your shared folders.

Jim

---

### Post by Anthony M on 2008-07-17
> **cariboo907 said:**
> THat's normal when using samba. Double click the windows network icon and you should see your workgroup, double click the workgroup icon and you should see your shared folders.

Jim

The "Windows Network" directory is empty.  I can boot the client computer into XP and view the ubuntu network, but cannot view the shared folders in Ubuntu.

---

