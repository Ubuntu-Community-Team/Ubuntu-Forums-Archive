---
title: "Setup Password Access"
date: 2008-04-29
forum: New to Ubuntu
---

### Post by handyguy33 on 2008-04-29
Hi all.

I have an Ubuntu server here at work. there are about two dozen xp users on my network that access it daily. What I want to do is setup a username/password login for them to access the server from now on. I know this is probably super easy, but I can't figure out what I have to do. If anybody knows a good how-to for this, I'd really appreciate it.

---

### Post by spiderbatdad on 2008-04-29
There are a dozen ways. Could you say a bit more about the type of server you are running...ie, apache2, and what your preferences are as an admin...are you looking for a GUI tool, or would you prefer to edit server config file...like setting up .htaccess for your directories.

---

### Post by handyguy33 on 2008-04-29
I'm running a samba file server. Basically it's a common place for us to store group projects. When I set up the server, I just followed a tutorial. I'm pretty sure I installed MySQL, but I don'rt recall setting up Apache. Whatever you think the path of least resistance is, I'll try.

---

### Post by spiderbatdad on 2008-04-29
Sorry I have not used Samba as a file sever, but browsing a little suggests it is fairly simple to set up authentication for users...
For example, under the global settings in smb.conf, setting security to user forces clients to authenticate.

I gave a quick perusal of these two links:
[http://www.redhat.com/docs/manuals/enterprise/RHEL-4-Manual/ref-guide/s1-samba-servers.html](http://www.redhat.com/docs/manuals/enterprise/RHEL-4-Manual/ref-guide/s1-samba-servers.html)
[http://www.redhat.com/docs/manuals/enterprise/RHEL-3-Manual/sysadmin-guide/s1-samba-configuring.html](http://www.redhat.com/docs/manuals/enterprise/RHEL-3-Manual/sysadmin-guide/s1-samba-configuring.html)

Yes it a redhat tutorial, but after all...we are all one big happy linux family.lol. The samba conf should be basically the same.

---

