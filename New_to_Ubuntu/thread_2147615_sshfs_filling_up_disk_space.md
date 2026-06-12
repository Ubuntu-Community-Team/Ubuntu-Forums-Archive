---
title: "sshfs filling up disk space"
date: 2013-05-22
forum: New to Ubuntu
---

### Post by Peterlorre on 2013-05-22
Hi all, 

Apologies if this is a noob question, but I'm running into trouble using sshfs to mount a remote folder (ubuntu 12.04 LTS; x64). The basic problem is that the remote folder is quite large, and although there isn't a problem initially, over a medium to long time I start getting errors indicating that root is running out of disk space. I assume that the OS is incorrectly counting remote files as local ones (that's what it looks like from the Disk usage analyzer), but I'm not sure how to prevent that from happening. The commands I'm using to mount the remote folder are: 

ssh hostname -l uname -Nf -L 20400:homemount:22

sshfs -o UserKnownHostsFile=/dev/null -o StrictHostKeyChecking=no -p 20400 \
   uname@localhost: ~/Desktop/PPS_Cluster/

Is the problem that I am mounting to the desktop? Intuitively it seems like this shouldn't be an issue, but perhaps someone clever can tell me what I am doing wrong.

---

