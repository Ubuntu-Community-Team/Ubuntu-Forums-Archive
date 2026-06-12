---
title: "USR/Home got me again can MV correct"
date: 2018-10-07
forum: New to Ubuntu
---

### Post by l6griffin on 2018-10-07
I recently bought a new computer with Ubuntu factory installed and have upgraded to 18.04. I backed up my old computer 17.04 after installing "luckyBackup", and restored to the new computer 18.04. Everything went just fine till I looked for the files on my new computer. The files are not in /home/larry they are in /home/larry/larry, so I need to move them. Will mv work to move the files to /home/larry. as

mv -n -s  /home/larry/larry /home/larry

without any more problems, files in use, system, tec., etc..

Thanks Larry

---

### Post by TheFu on 2018-10-07
Well, there's the way I'd do it which would have "files in use" issues and there's the way it can be done to avoid that problem, but it is more hassle.

Boot from a liveCD/flash drive with any recent Linux.  Mount the /home partition manually, then 
```
cd /home/larry/larry/ ; 
sudo mv * .* ../
```
The PWD and spacing for the move command are absolutely critical.

The way I'd do it would be to mv /home/larry /home/larry1, then mv /home/larry1/larry ../ ; then logout and login.
If the uid numbers were different between larry-old and larry new, I'd have to fix that.  The numbers matter.

And if you don't use a DE or complex desktop, there will be fewer issues.  I don't use any DE.

Clear as mud?

---

