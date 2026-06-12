---
title: "Looking for a slightly more complex backup script"
date: 2008-04-10
forum: Programming Talk
---

### Post by leezer3 on 2008-04-10
OK, what I'm looking to do here is beyond my capabilities (Not bad perl, ditto Bash scripts)
I'm trying to run a rather more complex backup than usual of a specific fileset on a destop machine onto my server.

In a nutshell, I'm looking for either a premade backup script that can do this, or advice on altering/ creating to suit :) :
1. Detect when a DCHP client connects to the router (192.168.1.186) The router is running OpenWRT, I think I can set things up so that it creates a file serverside at this point.
2. There should only be one backup per day, so the script needs to check if one already exists- Name files per date?
3. Run backup- Folder is smb://192.168.1.186/Backup
4. I'd like to upload the current week-end backup (IE. The one created on Sundays) to a remote FTP, keeping the most recent two on the remote server.

I considered running the script on the desktop side of things, but two problems- The file created is going to be C. 50-60mb, uploading this is going to take a while & I'd rather run this from the server. Secondly, the desktop is a Windows box, again I'd much rather keep things where I'm more comfortable and have better control.

Cheers

-Leezer-

---

### Post by stroyan on 2008-04-10
The backuppc package is very good at making periodic backups of clients,
including windows systems.  It has a web interface for configuring backup
clients and archive schedules.

It doesn't directly handle ftp of archives.  But you can add an arbitrary
post archive command that could ftp the archive to another system.

You can think of it as a really big perl script if you like.

---

