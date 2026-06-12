---
title: "How to recover encrypted Home directory?"
date: 2012-12-07
forum: New to Ubuntu
---

### Post by Houmie on 2012-12-07
I did the following and everything went successfull, but I still can't access it (Permission denied) why?

```
ubuntu@ubuntu:/tmp$ sudo ecryptfs-recover-private
INFO: Searching for encrypted private directories (this might take a while)...
INFO: Found [/media/ubuntu/2ce7caff-eb9a-40ac-8faa-50bce52117a7/home/.ecryptfs/hooman/.Private].
Try to recover this directory? [Y/n]: y
INFO: Found your wrapped-passphrase
Do you know your LOGIN passphrase? [Y/n] y
INFO: Enter your LOGIN passphrase...
Passphrase: 
Inserted auth tok with sig [3037702eb495e9e7] into the user session keyring
INFO: Success!  Private data mounted read-only at [/tmp/ecryptfs.NsnIktP1].
ubuntu@ubuntu:/tmp$ cd /tmp/ecryptfs.NsnIktP1/
bash: cd: /tmp/ecryptfs.NsnIktP1/: Permission denied

```

Thanks

---

### Post by roger_1960 on 2012-12-07
Could your sudo have timed out?

---

### Post by Houmie on 2012-12-07
> **roger_1960 said:**
> Could your sudo have timed out?

No my friend. It was fresh. I am going crazy. I cant access my data and my Ubuntu died on me this morning. :(

---

### Post by Houmie on 2012-12-07
no one? :(

---

### Post by insane_alien on 2012-12-07
try sudo cd /tmp/ecryptfs.NsnIktP1/ it's probably mounted with root permissions since you used sudo.

---

### Post by Houmie on 2012-12-07
> **insane_alien said:**
> try sudo cd /tmp/ecryptfs.NsnIktP1/ it's probably mounted with root permissions since you used sudo.

Tried ruuning it withour sudo and it doesnt allow it.

Also:

```

sudo cd ->
sudo: cd: command not found



```

---

### Post by insane_alien on 2012-12-08
if you use su to become root, then you should be able to cd into it.

or you could try chown to make your user the owner.

---

### Post by TheFu on 2012-12-08
What are the permissions on that directory/file?
**\ls -al** will show them provided no ACLs are used.

---

