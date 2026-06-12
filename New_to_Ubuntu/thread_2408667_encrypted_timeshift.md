---
title: "encrypted timeshift?"
date: 2018-12-21
forum: New to Ubuntu
---

### Post by foobuntu2 on 2018-12-21
Hi community,

I discovered timeshift for backups recently. Since I have an encryapted home folder I'm wondering how timeshift could encrypt my files when doing a backup. Currently timeshift will save the files in the /home directory but outside my home folder - unencrypted on the file system. Although all files belong to root it's now possible to restore my files from the storage device with external tools. For me this is a security vulnerablity. Therefore, I'm looking for a way to create encrypted backups with timeshift. One possible way I'm already aware of is the use of LUKS for the entire /home partition. Since I don't use LUKS currently this would create some hassle but ok. Do you guys know other alternatives?

Cheers.

---

### Post by TheFu on 2018-12-21
Welcome.

Some backup tools have encryption built-into their software.
Or you could simply store the backups onto encryption storage.

BTW, backups shouldn't be stored on the same physical disks that hold normal data.  It should be either a network server or an external drive that is not usually connected.  If using a network backup server, "pull" the backups to avoid any malware like cryptolocker from ruining your backups.  Locally connected disks are at risk from malware.

---

