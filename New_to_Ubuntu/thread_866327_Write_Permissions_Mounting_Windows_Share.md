---
title: "Write Permissions Mounting Windows Share"
date: 2008-07-21
forum: New to Ubuntu
---

### Post by XCan on 2008-07-21
After installing smbfs I've successfully mounted Window shares. However, whenever I create a file in the Window shares, the files turn into read only and owned by root/root. I can still rename the files, but can not overwrite them.

I imagine the issue is that they're owned by root, but how can one fix that by default since apparently one needs to sudo to mount. The command I use to mount is:

```
sudo mount -t cifs //server/dirA/ /mnt/Share -o username password
```

---

### Post by jbrown96 on 2008-07-21
You could try to change the owner. ```
sudo chown username:username -R /path/to/mount/location
``` for example I could change the ownership of where I have mounted a partition (I know it's not samba) with ```
sudo chown justin:justin -R /media/multimedia
``` That will give you all the permissions you need. Not sure if it is persistent though.

---

### Post by XCan on 2008-07-22
I tried what you wrote jbrown96. And it indeed changes all current files to the correct owner. However any new file I create still has the owner/grp root/root. The strange part is that I can do everything with the files _except_ overwriting them, i.e. delete, rename, move all work fine.

---

