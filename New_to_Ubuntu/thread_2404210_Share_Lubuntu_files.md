---
title: "Share Lubuntu files"
date: 2018-10-21
forum: New to Ubuntu
---

### Post by cybervigilante on 2018-10-21
I want to share files between two lubuntu machines on my local network. How do I do that? I looked at various tutorials and they're all different or don't apply, like one that said to install gksu, only the terminal says that's not available.

---

### Post by Dennis N on 2018-10-21
Here's my method:

Install **openssh-server** and **gigolo** on both computers.
Depending at which machine you are sitting, you will need the IP address of the other computer on the network. Know this beforehand.
Use gigolo to initiate and manage the connection to the other computer. Specify SSH as connection type. You need password to the OS user account that is on the remote IP address. Then you can browse the remote file system with file manager and do file manager operations.

Note: Optionally, Gigolo will bookmark info on machines you connect to, so you don't need to supply it over and over.

---

### Post by TheFu on 2018-10-21
There are many different ways to share files. 

If security is important and you might want to access the files over the internet, that is very possible using ssh, sshfs, sftp, scp, rsync methods.  These are all based on ssh-server.  Most Linux file managers understand "sftp://.... " URLs, but ssh-server needs to be setup on the remote system and probably want to use ssh-keys.  Because ssh uses strong encryption, there is a performance impact. How much depends on your CPU and which cipher is selected.  And of course, the network hardware matters too.  Some hardware will offload, Intel NICs, the moving of data better than network cards that don't do that (cough, realtek).

If you want the "native" way to do storage sharing that looks and feels just like local storage, use NFS. Since Linux/Unix are multi-user operating systems, the userids (the numbers 'id') and groupids need to be consistent across all the clients.  This isn't hard for just a few computers.  1000 is the first userid on Ubuntu, so if the same person handled the installs on every system and made the same account name, then it will be consistent.  On system A 1000 - system B 1000.  It is the numbers that matter, not the names. Same for groups.  NFS is the fastest option for transferring files.  NFSv3 only has IP addresses for security.  NFSv4 uses Kerberos, which is non-trivial to setup, but much more secure.  NFS is server to server, which is different than Windows file sharing.  Storage mounted via NFS is added for all users of the system and native file permissions are honored using the chmod, chown, and other commonly used POSIX file system capabilities.

Then there are the non-native methods to share files like using Samba/CIFS or plain FTP.  Please don't use Plain FTP. That protocol should have died in the mid-1990s.  Effectively zero security at all.  
CIFS is the protocol that Windows uses. It is user to server, so end-user authentication is necessary to access remote storage.  With some setup, Linux file managers will support smb:// .... URLs.  These are usually automatically mounted using something called GVFS which is slow.  Direct mounts using the CIFS protocol are almost as fast as NFS, but they are per user.  chmod doesn't work. Chown doesn't work.  Permissions are set at mount time or can be FORCED on the Samba-server.

So, those are a few options.  Any questions or ideas?  The number of computers, number of people would be helpful.

For Linux-to-Linux, I'd suggest using NFS.
For over the internet, I'd use sftp.  Every network OS has a great sftp client.
You can have multiple methods for the same storage.  I use ssh/sftp for almost everything, but also have NFS and Samba.  On the LAN, I use NFS almost always, but that requires setting it up in advance.  

sftp is 100% on the fly after installing openssh-server + fail2ban.  This is the easiest to setup and use, by far.

**Ninja'd by Dennis N!**

---

