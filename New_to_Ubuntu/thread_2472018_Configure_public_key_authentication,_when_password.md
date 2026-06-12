---
title: "Configure public key authentication, when password authentication is disabled"
date: 2022-02-15
forum: New to Ubuntu
---

### Post by boopalan2 on 2022-02-15
In a Linux system, "PasswordAuthentication" is disabled in "sshd_config" file, and "PubkeyAuthentication" is enabled.

System admin user creates new Linux user on the system. How the new user  ssh to the system? Because password authentication is already disabled.

And if the new user generates public key in his local machine, and try  to place in the Linux system, he could not place. Because currently both  Public key authentication and password authentication will not work.

Is there any workaround exists, to overcome this scenario?

---

### Post by #&amp;thj^% on 2022-02-15
[s][https://www.simplified.guide/ssh/disable-public-key-authentication](https://www.simplified.guide/ssh/disable-public-key-authentication)[/s]
I miss-read your post, but why hasn't  the System admin given them/you login creds.

---

### Post by boopalan2 on 2022-02-15
Though System admin provides credentials, "Password authentication" is already disabled in ssh.

---

### Post by #&amp;thj^% on 2022-02-15
>  "Password authentication" is already disabled in ssh.  I know I edited my post to reflect that.
**Are you the Admin?**

---

### Post by kevdog on 2022-02-16
If you can't login via password into your ssh server, then you need to provide the admin a copy of your public key.

---

### Post by MAFoElffen on 2022-02-16
> **kevdog said:**
> If you can't login via password into your ssh server, then you need to provide the admin a copy of your public key.

(Continued) So that that Admin or someone else who has Admin privileges can copy that user's key to the target device... For that User to be able to access. It can still be done remotely,in a round-about way, but not directly by the user who does not have access.

---

### Post by ActionParsnip on 2022-02-16
Someone else will need to add the user's public key to the user's account on the remote system for them

---

