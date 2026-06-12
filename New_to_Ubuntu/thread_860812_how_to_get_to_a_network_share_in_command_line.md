---
title: "how to get to a network share in command line"
date: 2008-07-15
forum: New to Ubuntu
---

### Post by Squish on 2008-07-15
Hey just wondering how I can change my directory to a network share on a differant computer?

Aye~

---

### Post by Yuki_Nagato on 2008-07-15
I generally use some form of transfer protocol first.  In my case, it is SSH.

```
ssh username@computer
```

It allows me to drop right into my computer securely.  It requires some setup, however.

_[It takes half an hour to setup]("https://help.ubuntu.com/community/SSHHowto")_


As far as something similar to a simple "cd," I do not know.

---

### Post by p_quarles on 2008-07-16
The answer depends on the kind of computer that's running the network share. If it's a Windows shared folder, it's as simple as using the Samba client. If you want to setup a Linux/UNIX computer to run a network drive, there are several things to choose from: NFS, SSHFS, and the already-mentioned Samba (there are others, as well, but those are the popular methods).

---

### Post by hyper_ch on 2008-07-16
you forgot sshfs ;)

---

### Post by p_quarles on 2008-07-16
> **hyper_ch said:**
> you forgot sshfs ;)
Erm, no I didn't?

---

### Post by hyper_ch on 2008-07-16
it was early morning, so I have a good excuse ;)

---

### Post by sdennie on 2008-07-16
If you've first navigated to the samba mount point via nautilus, it will also be available in ~/.gvfs.  It appears as just a normal file system in that case.

---

### Post by Squish on 2008-07-20
Vor Wins

Thanks Bros

---

