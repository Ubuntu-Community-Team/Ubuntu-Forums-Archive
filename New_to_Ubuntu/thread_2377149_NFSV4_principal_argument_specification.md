---
title: "NFSV4 principal argument specification"
date: 2017-11-09
forum: New to Ubuntu
---

### Post by bobk48 on 2017-11-09
When designating a principal argument, for a user, for the nfs4_setfacl command, I&#8217;ve found the two easiest and most effective ways of doing this are as follows-
$ nfs4_setfacl -a A::bob@localdomain:X hello
$ nfs4_setfacl -a A::1000:X hello
where:
1000 is the uid of the user you want to levy the ACL for
bob@localdomain is the user, and most importantly, the domain name that works for me.
These two ways got me around trying to determine what the domain name is for the server (or the client on which the above two alternative commands were given.)
if you know of a more effective, and easier way, let me know!

---

