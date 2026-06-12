---
title: "kubuntu svn+ssh"
date: 2012-07-30
forum: Programming Talk
---

### Post by icegood on 2012-07-30
Is there good way to make kdesvn work well passwordless with svn+ssh protocols?

---

### Post by dwhitney67 on 2012-07-30
You should be able to create a private/public key pair (refer to ssh-keygen).  Then place your public key on the remote system you wish to connect to.

Let me know if you require further details.

---

### Post by icegood on 2012-07-30
> **dwhitney67 said:**
> You should be able to create a private/public key pair (refer to ssh-keygen).  Then place your public key on the remote system you wish to connect to.

Let me know if you require further details.
Yes, i need futher details. I've already done it. Seems problem not only in password:
```

 p, li { white-space: pre-wrap; }  To better debug SSH connection problems, remove the -q option from 'ssh' in the [tunnels] section of your Subversion configuration file.

```
So,
1) where is Subversion configuration file

---

### Post by dwhitney67 on 2012-07-30
> **icegood said:**
> Yes, i need futher details. I've already done it. Seems problem not only in password:
```

 p, li { white-space: pre-wrap; }  To better debug SSH connection problems, remove the -q option from 'ssh' in the [tunnels] section of your Subversion configuration file.

```
So,
1) where is Subversion configuration file

Look in ~/.subversion directory.

---

### Post by icegood on 2012-07-30
> **dwhitney67 said:**
> Look in ~/.subversion directory.
found, set ssh to 
```

ssh = $SVN_SSH ssh -o ControlMaster=no

```
same result. Should i restart some daemon? Connot find appropriate one.

---

### Post by dwhitney67 on 2012-07-30
I'm not that familiar with the inner details of SVN (subversion), so when I needed to use it, I kept things simple... I didn't muck with any of the configuration file(s).

As for connecting to a remote server without the need to enter a password, I exported my SSH public key to the remote system.

---

