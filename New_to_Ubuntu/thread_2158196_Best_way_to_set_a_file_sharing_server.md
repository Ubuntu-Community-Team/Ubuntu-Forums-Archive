---
title: "Best way to set a file sharing server?"
date: 2013-06-28
forum: New to Ubuntu
---

### Post by GreatBunzinni on 2013-06-28
I'm looking for a way to let some users within a LAN to share files among themselves through a centralized repository.  

Currently, we've been using Dropbox for this purpose, but the storage space provided to free accounts is quite limited.  Moreover, it doesn't make much sense to send files across the internet throughout god knows where in the world just to make a file available to a computer connected to the same LAN and located right next to the sender. 

As an alternative, the first thought that came to mind was to set up a FTP server. As I have no experience setting up a file sharing server, let alone a FTP server, don't know where to start or even if this is the best way to offer this sort of service.

This service should make files available to linux and windows users, and it should limit access to only a set of authorized users.

For a newbie, does anyone know what's the best way to set up a file server on an Ubuntu installation?

---

### Post by mastablasta on 2013-06-28
well you need to install server (for windows users you need samba) and then depends how you plan on doing it (configure via text fiels or GUI). if you like GUI interface then install webmin to the server.

you might also look at Zentyal (Ubuntu based) and Open Media Vault (debian based). both are ment for small servers as you plan them.

---

### Post by Lars Noodén on 2013-06-28
If it is to be used only on the LAN and never over the Internet at large, then Samba will work for both Linux and other users.

[https://help.ubuntu.com/community/Samba](https://help.ubuntu.com/community/Samba)

If you want to access the files over the Internet, then you might look at SFTP.  It is built into the package OpenSSH-server so if you install that, then you have SFTP up and running.  There are SFTP clients built into most (all?) file managers these days, so you can access the SFTP server as if the files were local simply by pressing ctrl-L in the file manager and then entering the URI of your account. e.g. *sftp://greatbunzinni@198.51.100.23/home/greatbunzinni/ *

You should, however, be careful to avoid old FTP:

[list]
[*] [http://www.openlogic.com/wazi/bid/188103/Stop-Using-FTP-How-to-Transfer-Files-Securely](http://www.openlogic.com/wazi/bid/188103/Stop-Using-FTP-How-to-Transfer-Files-Securely)
[*] [http://blog.jdpfu.com/2011/07/10/why-you-need-to-stop-using-ftp](http://blog.jdpfu.com/2011/07/10/why-you-need-to-stop-using-ftp)
[/list]

---

### Post by Zill on 2013-06-28
The "native" file sharing system for Linux is [NFS]("https://help.ubuntu.com/lts/serverguide/network-file-system.html") and this works well if your network *only* has Linux clients.  See [SettingUpNFSHowTo]("https://help.ubuntu.com/community/SettingUpNFSHowTo")

However, if you have a "mixed" network, consisting of both Linux *and* Windows systems, then Samba is probably the way to go but I can't verify this as there are no Windows systems here. :-)
> **GreatBunzinni said:**
> ...For a newbie, does anyone know what's the best way to set up a file server on an Ubuntu installation?
p.s.  For a newbie, you joined Ubuntu Forums before I did, way back in 2005!!! ;-)

---

### Post by HermanAB on 2013-06-28
All the FTP server packages work 'out of the box'.  People only have configuration problems when they try to change something.

---

### Post by Horbo on 2013-06-28
Quick beginners guide to a samba server here: [http://ubuntuforums.org/showthread.php?t=1685718](http://ubuntuforums.org/showthread.php?t=1685718)

---

### Post by GreatBunzinni on 2013-06-28
> **Lars Noodén said:**
> If it is to be used only on the LAN and never over the Internet at large, then Samba will work for both Linux and other users.

[https://help.ubuntu.com/community/Samba](https://help.ubuntu.com/community/Samba)


I'm not familiar with Samba.  What advantages does it have over SFTP?


> **Lars Noodén said:**
> 
If you want to access the files over the Internet, then you might look at SFTP.  It is built into the package OpenSSH-server so if you install that, then you have SFTP up and running. 

Sounds good.  Is there any tutorial on how to set a SFTP server on an Ubuntu installation?

---

### Post by GreatBunzinni on 2013-06-28
> **Zill said:**
> The "native" file sharing system for Linux is [NFS]("https://help.ubuntu.com/lts/serverguide/network-file-system.html") and this works well if your network *only* has Linux clients.  See [SettingUpNFSHowTo]("https://help.ubuntu.com/community/SettingUpNFSHowTo")

However, if you have a "mixed" network, consisting of both Linux *and* Windows systems, then Samba is probably the way to go but I can't verify this as there are no Windows systems here. :-)

In this particular workgroup, unfortunately linux is the exception rather than the norm.

How hard is it to get Samba up and running, particularly with regards to a SFTP installation?


> **Zill said:**
> 
p.s.  For a newbie, you joined Ubuntu Forums before I did, way back in 2005!!! ;-)

Time does fly, but I'm still a newbie in a lot of areas.  Setting up a file sharing server is one of those things where I'm a hamfisted newbie.  For now, at least :D

---

### Post by GreatBunzinni on 2013-06-28
> **HermanAB said:**
> All the FTP server packages work 'out of the box'.  People only have configuration problems when they try to change something.

Sounds good.  Do you recommend any tutorial on the subject?

---

### Post by Lars Noodén on 2013-06-28
> **GreatBunzinni said:**
> Sounds good.  Do you recommend any tutorial on the subject?

It is unlikely that a tutorial is necessary.  If you go with SFTP, it is part of the package OpenSSH-server and so if you install that package you have an SFTP server running automatically.  

In addition to the file managers having SFTP support built in you can also connect with FileZilla or SSHFS.  SSHFS is a fancier SFTP client and will mount the remote system as if it were a local directory.  Linux, OS X and other systems can use SSHFS because it uses SFTP.  It's simple but works.

[https://help.ubuntu.com/community/SSHFS](https://help.ubuntu.com/community/SSHFS)

---

### Post by BBQdave on 2013-06-28
[**VSFTPD**]("https://security.appspot.com/vsftpd.html") and [**Filezilla**]("https://filezilla-project.org/") may be of interest to you :)

I have an old eMac that I use as a FTP server on a protected home network. Linux and Windows machines access it with Filezilla.

---

### Post by Cheesemill on 2013-06-28
If you don't have much Linux experience and all you need is a file server then I probably wouldn't use Ubuntu.

If you go for something like [FreeNAS]("http://www.freenas.org/") instead then you can be set up and serving files in minutes, all controlled by an easy to use web interface.

---

### Post by HiImTye on 2013-06-29
NFS is faster than SMB, but it requires Windows Services for Unix to be setup on the Windows boxes, and it won't work on unrooted Android, for instance.
SMB is fairly easy to set up, but it is very noisy and slow (I get 600-700kb/s on wifi).
SFTP (which is not based on FTP) is fast as well (I get 1300-1500kb/s on wifi), but it requires configuring SSH on all of the boxes. SSH has the added advantage of providing you with a secure way to connect over the internet (if you accept only key based logins).
FTP is very insecure (plain text passwords), but I'm not sure how fast it is compared to SFTP or NFS.
DLNA is the least secure, as it uses UPnP, which is like browsing the internet with Java enabled, but it requires configuration on only the sharing box. it is, however only really useful for sharing media.

keep in mind also, that with the exception of DLNA, you will need to get file permissions sorted as well.
[CENTER][COLOR=#333333][FONT=Roboto][/FONT][/COLOR][/CENTER]

---

