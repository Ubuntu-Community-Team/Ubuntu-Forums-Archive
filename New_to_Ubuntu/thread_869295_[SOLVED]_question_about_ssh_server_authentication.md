---
title: "[SOLVED] question about ssh server authentication"
date: 2008-07-24
forum: New to Ubuntu
---

### Post by ptn107 on 2008-07-24
I have set myself up for automatic authentication on my server via ssh, by adding my public key (id_dsa.pub) to the servers ~/.ssh/authorized_keys2 file.

Now when I ssh to my server I am no longer asked for a password, yet every tutorial I read says that if authentication is set up properly it should ask for the passphrase to my key.  Any ideas?

I have noticed that if I connect using the -v (verbose) option I eventually see:
```
debug1: Authentications that can continue: publickey
debug1: Next authentication method: publickey
debug1: Trying private key: /home/phil/.ssh/id_rsa
debug1: Offering public key: /home/phil/.ssh/id_dsa
debug1: Server accepts key: pkalg ssh-dss blen 433
debug1: No more authentication methods to try.

```

Does that mean it's working?

---

### Post by Xerp on 2008-07-24
If you didn't set a passphrase, then it won't ask you for one :)

---

### Post by ptn107 on 2008-07-24
I have typed a passphrase when I generated the private and public keys.

---

### Post by Vivaldi Gloria on 2008-07-24
authorized_keys2 is used in older implementations of OpenSSH. This file is still consulted for backward compatibility, but it has been deprecated. Only authorized_keys should be used to store public keys for users. Multiple keys are allowed in authorized_keys.

I don't know if using authorized_keys2 is the cause of your problem but try using authorized_keys.

---

### Post by ptn107 on 2008-07-24
> **Vivaldi Gloria said:**
> authorized_keys2 is used in older implementations of OpenSSH. This file is still consulted for backward compatibility, but it has been deprecated. Only authorized_keys should be used to store public keys for users. Multiple keys are allowed in authorized_keys.

Yeah I am aware of this.  I've been reading through SSH: The Secure Shell by O'Reilly and it makes mention of this.  However it is not the problem.  When using authorized_keys it still doesn't ask me for anything when I connect.  I suspect that Ubuntu's default configuration for ssh has something to do with this.

---

### Post by Vivaldi Gloria on 2008-07-24
You have not added the key to shh-agent, have you? It won't ask the passphrase in that case.

---

### Post by Mister.Vash on 2008-07-24
Your ssh password is stored in the gnome-keyring in hardy now.  If you want to be prompted for a password run gconf-editor navigate to the /apps/gnome-keyring/daemon-components/ssh key and uncheck it.  I don't recall if this is a dynamic change or requires a restart of gnome

---

### Post by ptn107 on 2008-07-27
> **Mister.Vash said:**
> Your ssh password is stored in the gnome-keyring in hardy now.  If you want to be prompted for a password run gconf-editor navigate to the /apps/gnome-keyring/daemon-components/ssh key and uncheck it.  I don't recall if this is a dynamic change or requires a restart of gnome

Yep this was the reason.  Thanks.

---

