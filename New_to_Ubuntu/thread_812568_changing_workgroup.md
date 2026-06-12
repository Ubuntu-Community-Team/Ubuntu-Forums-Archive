---
title: "changing workgroup"
date: 2008-05-30
forum: New to Ubuntu
---

### Post by frost151n on 2008-05-30
hey,
ok here's the thing, i right clicked documents and selected share.
now in network... here's what it looks like
MMB-L (thats me) windows network
documents        be bt mshome
                       MMB-L
                       documents
then i deleted documents from system>admin.>shared folders
but mmb-l and mshome are still there albeit empty.
how do i join 'be' network and delete mmb-l and mshome????

p.s. until this past monday, i ddn't even know wht command line is... be gentle

*oh, im on 7.10

---

### Post by ajmorris on 2008-05-31
hey there,
to change your workgroup, edit the file /etc/samba/smb.conf and in the global section, change worgroup = <WORKGROUP> to whatever you want. The reason why those other ones displayed after removing your shares, is because there we no longer any shares in those workgroups.

AJ

---

