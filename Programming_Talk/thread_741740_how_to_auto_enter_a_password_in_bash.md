---
title: "how to auto enter a password in bash?"
date: 2008-04-01
forum: Programming Talk
---

### Post by micahkoga on 2008-04-01
i'm creating a script that uses rsync over ssh. everytime i run the script it asks for the ssh password. is there a way where i can put the password in the script so it won't ask everytime?

---

### Post by ghostdog74 on 2008-04-01
ssh is meant to be used passwordless. set up the appropriate ssh keys between your comp and your destination server. Review your SSH manual for more info.

---

### Post by bvmou on 2008-04-01
You can enable passwordless login over ssh by adding your public key to the authorized_keys file in the remote host.  I do something like:

```
ssh-keygen -t rsa
```
(This generates a public-private key pair, you can accept defaults)

```
scp ~/.ssh/id_rsa.pub user@remotehost.com:

ssh user@remotehost.com

cat id_rsa.pub >> .ssh/authorized_keys
```

These commands, 1) copy the public key to remote user home directory, 2) ssh into remote host, and then 3) append your public key to the authorized key list).  That should end password prompts.  It is also useful for things like sshfs.

---

