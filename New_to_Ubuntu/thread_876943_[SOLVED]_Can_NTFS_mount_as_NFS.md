---
title: "[SOLVED] Can NTFS mount as NFS?"
date: 2008-08-01
forum: New to Ubuntu
---

### Post by tmcmulli on 2008-08-01
I'm mounting some remote drives NFS, unfortunately, there are formatted NTFS, and I'm getting an error when starting the nfs-kernel-server that the drive does not support NFS Export.

I'm assuming that this means I can't mount an NTFS drive, but before I move the data, reformat the drive ext3, and move it back, I just wanted to see if anyone can give me a definitive answer.

Thanks!!!

---

### Post by arrrghhh on 2008-08-19
short answer: no.

long answer: yes, with a lot of fiddling.  there's several different ways, 1 would be to use the most updated kernel (WAY more updated than ubuntu is currently at... the newest git kernel image has it built in & doesn't depend on FUSE).  another way would be to compile the newest ntfs-3g package (the one in the repo's won't work).  and the final and least initially efficient in the short run but most efficient in the long run would be to ditch NTFS entirely (assuming you have no need for it.)

edit:
just saw your post, and i actually figured out an easy way to do it.  install the nfs-user-server instead of nfs-kernel-server on the server and ntfs mounts work w/o any additional hassle.  plus, there is no exportfs so when you edit /etc/exports all you have to do is restart /etc/init.d/nfs-user-server!

but ext3 is much better with user ids permissions no fragmentation etc so you're better off in the end doing what you did ;)

---

### Post by tmcmulli on 2008-08-19
Thanks, I already figured that out, moved the data off the drives, reformatted them to ext3, and happily mounted them NFS.

---

