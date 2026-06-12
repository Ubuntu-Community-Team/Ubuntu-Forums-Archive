---
title: "How to back up to CD and network with grsync?"
date: 2008-06-29
forum: New to Ubuntu
---

### Post by stig on 2008-06-29
I've had a look at grsync for backing up files and folders. But can I make the destination in grsync (a) a CD, and (b) a networked computer? I unsuccessfully tried several things and have exhausted my ideas now! There isn't any relevant info on the grsync web site as far as i can see and I didn't find anything on the web.

---

### Post by vanadium on 2008-06-29
A networked computer is not any problem. rsync, the application behind grsync, can "talk" directly to remote machines over ssh. Alternatively, a remote system can (usually) be mounted on the local file system, and then the synchronisation can happen as if the remote data were on your local machine. For more specific help, we need specific information.

For CD it is another story. rsync (and grsync) are not suited to back up to CD. For backing up to CD, you should just burn the data on the CD using a CD burning application like Brasero.

---

