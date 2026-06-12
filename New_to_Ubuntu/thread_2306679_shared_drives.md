---
title: "shared drives"
date: 2015-12-17
forum: New to Ubuntu
---

### Post by graham.prout on 2015-12-17
i am setting up a media and file sharing server with ubuntu and was woundering if its possible to have the drives there will be 10 ecternal usb ranging from 250gb to 2tbs showing on then network in the root like a computer does i.e. npot having to click on the server and then the share?

I will be installing samba, ntfs and plex and possible the itunes server.

I am using a Dell R90L which is 1ghz amd cpu 2gb ram 1gb network and wifi 40gb internal ide drive =, 7 port mains powered usb hub all connected to a surge protected extention cable mounted in the attic.

i can setup the normal samba shares and everything else.

---

### Post by TheFu on 2015-12-18
No. but you can automatically mount the storage from client workstations, so nobody needs to know it is networked storage.
If the client machines are OSX, Linux, Unix, use NFS instead of CIFS. You'll thank me.

---

