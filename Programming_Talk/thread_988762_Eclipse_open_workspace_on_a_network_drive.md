---
title: "Eclipse: open workspace on a network drive"
date: 2008-11-20
forum: Programming Talk
---

### Post by zpzpzp on 2008-11-20
Hi

I have mapped a network drive in Ubuntu. There is a workspace on the network drive which I wish to open in Eclipse. However Eclipse does not recognize the network drive. The highest level I can go is "File System". Is there a way to use a workspace on the network drive?

Thanks a lot.

Paul

---

### Post by MisterPD on 2010-01-21
Bump. I need this as well.

---

### Post by dwhitney67 on 2010-01-21
Where is your network drive mounted on your system?  Run the 'mount' command to find out.

Typically it is mounted under /mnt, but could also be mounted under /media, if using an external drive.

Either way, these paths are relative to the root directory of /, thus you should be able to navigate to them using the Eclipse workspace browser, unless you lack the appropriate permission level to do so.

---

