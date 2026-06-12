---
title: "Files replication"
date: 2014-04-04
forum: New to Ubuntu
---

### Post by gopukrishnan on 2014-04-04
Hi,

I am looking for a suitable method to replicate website files (master-master) between two webservers. I used glusterfs previously and had some issues especially when one of the server restarts. Found that unision with incron works but I guess incron wont recursively check the subfolders. I can see some master-slave replication methods but I need master-master. Please suggest me a nice method for the master-master files replication.

Thanks,

---

### Post by TheFu on 2014-04-04
For data files only?  csync.  I've never used it, just providing options.  I've used 2-way rsync and that works, provided the serve times are synced and there aren't too many file changes.  For a nominal webserver, this is fine.

But I'd deploy a SAN and just keep the files in a single location with great backups if the files changed all the time.  I'd probably setup multiple read-only access and 1 write-access node.  After all, any uploaded files need to be pushed to a different 2nd-level domain for web security anyway.

For databases - well, that is a completely different.

---

### Post by gopukrishnan on 2014-04-04
Hi TheFU,

Thanks for your suggesion. Yes I am checking only for data files. I have already implemented master-master mysql replication and it works great. I shall check the csync.

---

### Post by TheFu on 2014-04-04
A SAN really would be better - even if just NFS.  You could run rsync backups over a different network to other server, setup monitoring so if the SAN goes down, then serve files locally.

It is hard to provide a "solution" vs "options" without knowing the physical limits of the servers, connectivity, amount of data involved and budget.  A $5k NAS solution can really work miracles for stuff like this.

---

