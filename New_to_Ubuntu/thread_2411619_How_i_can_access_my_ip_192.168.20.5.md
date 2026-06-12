---
title: "How i can access my ip 192.168.20.5"
date: 2019-02-01
forum: New to Ubuntu
---

### Post by a.mushtaqali on 2019-02-01
In windows 10 it is very easy to access ip address. In start just type my ip address and my media folder open. 
I am new to linux world. How can i access on ubuntu 18.9. Please help me.

---

### Post by TheFu on 2019-02-02
Welcome to the forums.

What does "access ip address" mean?    That is confusing.

* Find the value?
* Connect to a web server on it?
* Connect to an NFS server on it?
* Connect to a CIFS server on it?
* Connect to a nextcloud server on it?
* Connect to an ssh/sftp/scp/rsync server on it?
* Connect to a remote desktop on it?
* there are thousands of different protocols where an IP address would be used to access a remote system. Please help us understand your intention.

Also, what is ubuntu 18.9?  There isn't any release with that version.  People new to Ubuntu should stick with LTS releases - that would be either 18.04 or 16.04.  All other releases have 6-9 months of support from the date they were released. Basically, by running a non-LTS, the owner must upgrade every 6 months to the next version to keep support.

If I were a betting person, I'd say you need to open any file manager, then either "Browse Network" or type in smb://192.168.20.5 into the URL field. There are 20+ different file managers, but most work the same way. 

You could setup name resolution so you don't need to type in any IP, but just a hostname instead.  Linux is designed to scale on networks with 100,000 systems, so having all of them broadcasting "I"m here", "I'm here" doesn't make for a scalable network.  That is how Windows file servers have worked for a long time.  Because all the home users joining the Linux revolution, typically having very small networks, a solution called "avahi" was created for Linux systems to announce which services they support on the network.  If avahi is working on the client and the server, then they should find each other by accessing {hostname}.local ... so if my computer hostname is "foo", then inside the file managers, I'd enter **smb://foo.local/** to access CIFS file sharing.  This assumes avahi is working and that cifs file sharing was setup on the other machine and that the cifs/smb client was installed on the desktop.  

No servers run automatically on Ubuntu. They must be installed, configured and run.  It is also the responsibility of the admin to enable any firewalls needed whenever a new service is configured. Nothing is automatic. The user has complete control.  That is a plus and a minus, depending on your point of view.

---

