---
title: "Cannot copy to an external HD"
date: 2012-08-21
forum: New to Ubuntu
---

### Post by Isal on 2012-08-21
I just bought a new HDD, formatted it with my Mac in OSX Extended. Set the permissions to Read and Write for Everyone but my Ubuntu machine keeps telling me that the disk is "read only" if I try to copy something. 

Is it because it is not FAT32?

Help!

---

### Post by nothingspecial on 2012-08-21
If you have formatted it with hfs+ then you will need to disable journaling if you want to mount it read write with Ubuntu.

---

### Post by Isal on 2012-08-21
Tried that. Disabled Journaling in disk utility. Still the same thing.

---

### Post by Yellow Orange on 2012-08-21
Linux+HFS is bad idea. Drivers are quite unstable. Even you handle it now, nobody guarantee stable work and your data safety.

---

### Post by c_cinq on 2012-08-21
it could be that user is not the owner;  try re-assigning user:group

---

