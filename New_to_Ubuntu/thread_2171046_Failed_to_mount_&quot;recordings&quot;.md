---
title: "Failed to mount &quot;recordings&quot;"
date: 2013-08-28
forum: New to Ubuntu
---

### Post by deanie44 on 2013-08-28
Hi everyone.  I connected an external hardrive to my pc.  I changed it from root ownership to gina55.  Mythtv can read and write to it.  The problem is that when I restart the computer,  It will not mount anymore.  I receive an error message:[COLOR=#800000]Error mounting: mount exited with exit code 1: helper failed with mount: only root can mount /dev/sdb2 on /media/sdb2[/COLOR].  How do i correct this problem.  I have recordings on the partition.  Any assistance will be helpful.  Thank you deanie44

---

### Post by mikewhatever on 2013-08-29
What are the permissions of /media/sdb2 - 'ls -ld /media/sdb2'?

---

### Post by deanie44 on 2013-08-29
mikewhatever, thank you for answering my post.  the outcome of ls -ld /media/sdb2 is drwxr-xr-x 2 root root 4096 Aug 28 09:13 /media/sdb2.  Any suggestions?  Thank you.  deanie44

---

### Post by deanie44 on 2013-08-31
Thanks everyone who answered my post.  I solved the problem.  deanie44

---

