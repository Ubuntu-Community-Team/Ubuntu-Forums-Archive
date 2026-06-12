---
title: "Encryped Home folder mounts over other fs"
date: 2011-11-04
forum: New to Ubuntu
---

### Post by carrarin on 2011-11-04
Hello everyone, 

I have fs setup for each of the major directories in my home folder: I have a music filesystem, documents filesystem, etc... I modified the /etc/fstab so that the filesystems mount on the appropriate mount points, rebooted my computer, and took a look. I found that my drives did not appear to mounted, ie. my music was not in the Music directory... My drives were mounted, but the data was not accessible. 

I did some digging and found that when you have an encrypted home folder, the home folder mounts last...its one of the last fs to be mounted. Is there some way that I can mount these other fs over my encrypted home folder... 

Is there any way to resolve this issue? If there is not a solution, who can I send my hate mail to? 

Thanks, buddy!

---

