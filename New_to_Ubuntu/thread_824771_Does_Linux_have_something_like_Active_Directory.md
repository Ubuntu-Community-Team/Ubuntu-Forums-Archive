---
title: "Does Linux have something like Active Directory?"
date: 2008-06-10
forum: New to Ubuntu
---

### Post by diablo75 on 2008-06-10
I'm wanting to do some reading about setting up a network of computers, one being a server, and some other client PCs that will authenticate against that server, as well as administer group policies and permissions against the user accounts.  I had a little practice at this with Windows 2003 Server in technical school a year ago, but that was about it.  And we never played with Linux in class (well... I did, nobody else did).

One of the things about active directory that I liked was the large number of permissions you could check off or uncheck for each user account.  Things like the ability to be able to shut the computer down (or not), permission to access certain aspects of the OS (like the command line, or the control panel), and other stuff like that.  How do you set up things like this in Linux/Ubuntu?

---

### Post by Golem XIV on 2008-06-10
If you're using Hardy, try System -> Administration -> Authorizations

---

### Post by diablo75 on 2008-06-10
I'm away from my Ubuntu PC till the afternoon, so I'm just trying to kill time with reading material.  Is there some community documentation out there about this stuff I could read?

---

### Post by ukripper on 2008-06-10
> **diablo75 said:**
> I'm wanting to do some reading about setting up a network of computers, one being a server, and some other client PCs that will authenticate against that server, as well as administer group policies and permissions against the user accounts.  I had a little practice at this with Windows 2003 Server in technical school a year ago, but that was about it.  And we never played with Linux in class (well... I did, nobody else did).

One of the things about active directory that I liked was the large number of permissions you could check off or uncheck for each user account.  Things like the ability to be able to shut the computer down (or not), permission to access certain aspects of the OS (like the command line, or the control panel), and other stuff like that.  How do you set up things like this in Linux/Ubuntu?

Some reading material on OPENLDAP setup. 
OpenLDAP works like Active directory.
[http://ubuntuforums.org/showthread.php?t=640760](http://ubuntuforums.org/showthread.php?t=640760)

---

### Post by diablo75 on 2008-06-10
Thanks for the link!  Though, not knowing much about this, I get the impression LDAP exists so Linux servers can accommodate networks that mostly run Windows machines.  Is there an Ubuntu-only kind of permissions administration?  I'd like this network to run Ubuntu only, actually.  Active Direction is simply what I'm (barely) familiar with, but I'm not exactly seeking to use it.

---

### Post by ukripper on 2008-06-10
> **diablo75 said:**
> Thanks for the link!  Though, not knowing much about this, I get the impression LDAP exists so Linux servers can accommodate networks that mostly run Windows machines.  Is there an Ubuntu-only kind of permissions administration?  I'd like this network to run Ubuntu only, actually.  Active Direction is simply what I'm (barely) familiar with, but I'm not exactly seeking to use it.

use NFS server for ubuntu only network instead of samba server.
[http://ubuntuforums.org/showthread.php?t=597056](http://ubuntuforums.org/showthread.php?t=597056)

---

### Post by ukripper on 2008-06-10
> **diablo75 said:**
> Thanks for the link!  Though, not knowing much about this, I get the impression LDAP exists so Linux servers can accommodate networks that mostly run Windows machines.  Is there an Ubuntu-only kind of permissions administration?  I'd like this network to run Ubuntu only, actually.  Active Direction is simply what I'm (barely) familiar with, but I'm not exactly seeking to use it.

you can use NFS server for ubuntu only network instead of samba server. you can use Active directory for ubuntu only network as well and authenticate ubuntu machines using samba.

Active directory has plenty of options and easy administration if you have mixed network( means ubuntu and windows) then use active directory. but if you just planning to run ubuntu server with primary domain controller then NFS server and OpenLDAP would work alright. Adminitration won't be as easy as active directory for domain controller.

[http://ubuntuforums.org/showthread.php?t=597056](http://ubuntuforums.org/showthread.php?t=597056)

---

### Post by diablo75 on 2008-06-10
Thanks for the help!  Now I've got plenty to read.  :)

---

### Post by timcredible on 2008-06-10
> **diablo75 said:**
>   Is there an Ubuntu-only kind of permissions administration? 

no, linux isn't like windows, everything is open and can be used/adopted by all. no proprietary junk here.

---

