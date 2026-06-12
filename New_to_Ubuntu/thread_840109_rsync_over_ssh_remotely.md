---
title: "rsync over ssh remotely"
date: 2008-06-25
forum: New to Ubuntu
---

### Post by MaximB on 2008-06-25
I want to make a script on my work machine that backups all other Linux machines in my work and puts them to a remote storage (which is also a Linux machine).

I know that regular rsync doesn't work when trying to backup from a remote to a remote locating, but i read that rsync over ssh should work.

I've tried to backup with "scp" and it works , but I prefer to use rsync for this purpose.

I've tried this command :

```
ssh root@machine1 rsync -avz -e ssh /home/ root@storage:/path/to/dir
```

and I get this error :

```
Permission denied, please try again.
Permission denied, please try again.
Permission denied (publickey,gssapi-with-mic,password).
rsync: connection unexpectedly closed (0 bytes received so far) [sender]
rsync error: unexplained error (code 255) at io.c(635) [sender=3.0.2]

```

I don't know why I get this error as the passwords are ok, and I don't remember ever needing a public key, it authenticates by password.
I can ssh to both machines without public key.
Maybe the command is wrong ?
 

Again I remind you, the script will be run out of my machine and it should backup all others remote machines (and mine as well) to a remote storage locating.

Thanks.

P.S
We are using redhat, not that it should matter , but just don't give me Debian/Ubuntu specific packages or commands.

And yeah I intend to make this script with "autoexpect" this should memorize the commands I write and should avoid the "passwords in scripts over ssh" problem.

---

### Post by hyper_ch on 2008-06-25
does the remote ssh server only allow access with a key?

---

### Post by MaximB on 2008-06-25
No.
I can access ALL our servers via ssh with password only.

---

### Post by hyper_ch on 2008-06-25
this is strange... what if you build up a normal ssh connection?
```

ssh root@storage

```?

---

### Post by MaximB on 2008-06-25
> **hyper_ch said:**
> this is strange... what if you build up a normal ssh connection?
```

ssh root@storage

```?

As I've said no problems here :

```
[root@machine1 ~]# ssh root@storage
root@storage's password: 
Last login: ########
[root@storage ~]# 

```

---

### Post by hyper_ch on 2008-06-25
this is really strange ;(

---

### Post by MaximB on 2008-06-25
Help still needed.

---

### Post by hyper_ch on 2008-06-25
does it work to other servers?

All I can find is:

ssh -e ssh REMOTE LOCAL

I have not seen one example like

ssh -e ssh LOCAL REMOTE

it might be that with using an alternate shell you can only used REMOTE -> LOCAL...

---

### Post by MaximB on 2008-06-25
> **hyper_ch said:**
> does it work to other servers?

All I can find is:

ssh -e ssh REMOTE LOCAL

I have not seen one example like

ssh -e ssh LOCAL REMOTE

it might be that with using an alternate shell you can only used REMOTE -> LOCAL...

I don't need any example for "ssh -e ssh LOCAL REMOTE".

I need an example for "ssh -e ssh REMOTE REMOTE".
If you didn't yet get it.

---

### Post by hyper_ch on 2008-06-25
I don't think you can set the target as remote...

---

### Post by MaximB on 2008-06-26
> **hyper_ch said:**
> I don't think you can set the target as remote...

With "scp" I can do this.
I just think that rsync is better for this purpose IF I'll manage to get it working.

---

