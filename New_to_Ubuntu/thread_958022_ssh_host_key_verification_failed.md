---
title: "ssh host key verification failed?"
date: 2008-10-24
forum: New to Ubuntu
---

### Post by garyed on 2008-10-24
I have 3 computers hooked up to a router.
A - Wired Desktop
B - Wired Desktop
C - Wireless Laptop

Using SSH

A + C connect passwordless using either one as host.
A connects to B using password
B will not connect to A & it gives this message:

Please contact your system administrator.
Add correct host key in /home/gary/.ssh/known_hosts to get rid of this message.
Offending key in /home/gary/.ssh/known_hosts:3
RSA host key for 192.168.1.136 has changed and you have requested strict checking.
Host key verification failed.

I know how to generate the id_rsa.. but I don't know if that will effect my other connections or even if that will work.
Also I have the same user name on all my computers so I don't even know which computer is being referred to in the error message.

Any ideas

---

### Post by doas777 on 2008-10-24
just delete /home/gary/.ssh/known_hosts . when your hosts connect next, ssh will ask if you wish to cache their keys, and regen the file.

good luck,
Franklin

---

### Post by garyed on 2008-10-24
> **doas777 said:**
> just delete /home/gary/.ssh/known_hosts . when your hosts connect next, ssh will ask if you wish to cache their keys, and regen the file.

good luck,
Franklin
On which computer do I delete "known_hosts"
file on? The one that I ran the ssh command from(B) or the one I'm trying to connect to(A). Also will deleting the know_host file have any effect on the connection between A & C ?

---

### Post by doas777 on 2008-10-24
ok heres whats going on. when you connect from A to B, A will cache B's Key. in this case, computer A's Key changed, and no longer matches the one B holds. since the key has changed, ssh assumes that someone is hijacking the connection, and refuses connection.

to clear the old/bad key value you would delete known_hosts on PC B. then next time you connect to A from B (or to or from C) the file will be created.

the only affect this will have on your sshing, is that next time you connect to any box from B, it will ask if you want to cache the key. say yes and it won't ask again.

[http://ubuntuforums.org/archive/index.php/t-853186.html](http://ubuntuforums.org/archive/index.php/t-853186.html)

good luck,
Franklin

---

### Post by acidsolution on 2008-10-25
Suppose computer A tries to connect to Computer B and A get this error message 
than just go and delete file /home/gary/.ssh/known_hosts

Now whenever A tries to connect to B it appends new fingerprint of B in this file.

---

### Post by tgalati4 on 2008-10-25
Instead of deleting the entire file, you can simply delete some entries in the file starting from the top.  Since the actual IP addess is encoded, you are deleting these lines blindly, but that way you can preserve the keys for other machines on the network.

This is a common problem on a local subnet (Local Area Network or LAN) where the IP addresses get assigned automatically.  When the addresses get reused, for example 192.168.1.100, the stored keys on a given ssh machine will no longer match giving you an error message.

You can avoid this by assigning fixed IP addresses for those machines that routinely need to connect via ssh.

---

### Post by garyed on 2008-10-25
Excellent!
That worked like a charm.
Now what if I do the passwordless logon from B to A like I did from A & C
using this code on B.
```
ssh-keygen -t rsa 
```
and then:
```
 ssh-copy-id -i ~/.ssh/id_rsa.pub user@remotehost(A)
```
Will that effect the passwordless login between A & C ?

---

