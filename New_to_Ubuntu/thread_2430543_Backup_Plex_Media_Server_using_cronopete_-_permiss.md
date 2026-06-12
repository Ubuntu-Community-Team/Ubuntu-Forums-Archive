---
title: "Backup Plex Media Server using cronopete - permission denied..."
date: 2019-11-03
forum: New to Ubuntu
---

### Post by redrock14 on 2019-11-03
Hi -

I have Ubuntu 18.04 installed on an Intel NUC8i7.  This is currently set up as my Plex Media Server (PMS).  I am totally new to Ubuntu in general and so far, after quite some trial and error, I have everything finally working properly.  I have learned a great deal so far, but this has me stumped: 

I found Cronopete for its similarity to TimeMachine which I am familiar with.  Cronopete is doing exactly what I expect, all is good.  It is backing up everything in my home folder and I am happy with that.  However, PMS stores all metadata, configs, and so forth in the /var/lib/plexmediaserver/ folder.  

When I tell Cronopete to include that folder in the list of folders to backup and I invoke a backup, Cronopete complains with a "permission denied" message.  There is an awful large amount of info in this folder, that I would really like to back up.  Suggestions would be appreciated.

thanks!

---

### Post by TheFu on 2019-11-04
How are your skills with Linux/Unix?  Is it just Ubuntu you are new to or all Unix-like OSes?

I know nothing about Cronopete, but if you are doing backups under your own userid, it won't work.

Plex runs under a different userid.  Ubuntu, Linux, Unix are all multi-user.  Everything on the systems is built around that idea.  File and directory permissions are the cornerstone for all Unix OS security.  Backups need to include owner, group, permissions, ACLs and the data. Having just the data alone isn't sufficient.  To capture all that data, backups need to be run as root or with sudo.

PMS will store all sorts of stuff, if you let it.  It is possible to turn off the storage-wasting stuff.  There are guides for that. How many "fan banners" do we need?  If you let it, plex will create tiny images so ffwd and rwnd can show images.  That's a trade-off. Images for storage.   Which we get to/have to backup.

---

