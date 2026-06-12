---
title: "PC -to -PC LAN file transfer?"
date: 2011-09-27
forum: New to Ubuntu
---

### Post by Toafan on 2011-09-27
Hey all --

I've got two PCs (running Ubuntu) that I'm trying to network directly to each other so that I can transfer files between them. I know this will probably require some manual config.
I've never done this before, so I was wondering what commands to use. I've managed to get them ping-ing each other, but have no Idea how to get files from one to another, since I already tried rget and rput (don't exist).

Any tips?

Thanks

---

### Post by spiky001 on 2011-09-27
Hi you will need to install ssh open server on machines, it is in package manager.  [https://help.ubuntu.com/community/SSH](https://help.ubuntu.com/community/SSH)

---

### Post by lisati on 2011-09-27
Congession time: I've never done it via the command line.

When I first started using Ubuntu back in 2007, I discovered Samba - I was using mainly Windows back then - and have used it ever since. I have Samba installed on the Ubuntu boxes, and use Nautilus (from "places" on the classic Gnome menu) in a similar fashion to Windows Explorer.

---

### Post by Toafan on 2011-09-27
Thanks all.
I didn't get the answer I wanted, but I can't say I'm surprised. Sometimes, you just have to do it the hard way.
(Although, it's a moot point now since another way to accomplish my goal came up.)

---

### Post by dwasifar on 2011-09-27
I'm surprised no one mentioned scp.

Let's say you're transferring a file from 192.168.1.100 to 192.168.1.101 on your local network.

From the receiver:

```
scp 192.168.1.100:/path/to/file/filename.ext /path/to/save/file/ 
```

Or, from the sender:

```
scp /path/to/file/filename.ext 192.168.1.101:/path/to/save/file/
```

If the systems know each other by hostnames, you can use the hostnames instead of the IPs.  You can also use wildcards in the filenames, or -r to copy whole directories.

---

### Post by Miljet on 2011-09-27
I use NFS to accomplish this. This is a link to the best NFS tutorial I found.
[http://mostlylinux.wordpress.com/network/nfshowto/](http://mostlylinux.wordpress.com/network/nfshowto/)

---

### Post by anewguy on 2011-09-27
> **Toafan said:**
> Thanks all.
I didn't get the answer I wanted, but I can't say I'm surprised. Sometimes, you just have to do it the hard way.
(Although, it's a moot point now since another way to accomplish my goal came up.)

I hope you understand, but your reply is very insulting.

(1) Why aren't you surprised?  Sounds like you had a preconceived notion of what you were after but didn't state that.

(2) The hard way?  Be nice if you could explain how you got to that conclusion.

(3) If it's moot because you found another way, why don't you post it so others might know?

Obviously you didn't state everything in your opening posts or you probably would have gotten answer along the way of what you wanted.

Dave

---

### Post by dwasifar on 2011-09-27
> **Miljet said:**
> I use NFS to accomplish this. This is a link to the best NFS tutorial I found.
[http://mostlylinux.wordpress.com/network/nfshowto/](http://mostlylinux.wordpress.com/network/nfshowto/)

Yeah, I use NFS too.  I have a machine set up as a file server and everything else connects to its nfs shares.  I just didn't get the feeling the OP wanted to set up permanent shares.

---

### Post by ubudog on 2011-09-28
Thread closed.

---

