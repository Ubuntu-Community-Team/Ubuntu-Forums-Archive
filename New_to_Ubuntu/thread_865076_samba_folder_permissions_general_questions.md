---
title: "samba folder permissions: general questions"
date: 2008-07-20
forum: New to Ubuntu
---

### Post by badperson on 2008-07-20
Hi,

I've been playing around with a samba server, and have a question: do folder permissions have to do with the samba configurations, or do they have to do with the settings on the machine where the folder is created? 

I've had a number of issues with my samba server; I can read files from any machine on the network, but if I create folders from a machine other than the server, I can't write to that folder or delete that folder from the other machines. 

Also, the other day I tried to upload some photos to flickr directly from the server, and it wouldn't let me do that; I had to copy them to the local machine and upload. 

I've played around with the permissions settings on the server, i've given everybody read/write/delete access...is it something I need to setup in the  samba.conf file?

thanks,
bp

---

### Post by jonabyte on 2008-07-20
Try adding these to the shared folder section:

```

create mask = 0777
directory mask = 0777
```

---

