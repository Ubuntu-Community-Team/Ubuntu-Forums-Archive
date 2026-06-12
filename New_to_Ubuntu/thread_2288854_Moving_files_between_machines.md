---
title: "Moving files between machines"
date: 2015-07-30
forum: New to Ubuntu
---

### Post by ben152 on 2015-07-30
Can someone point me in the right direction on how to move files between machines that have no GUI? I am familiar with SFTP and transferring files between two Ubuntu machines with a GUI.

We use Ubuntu here at work and our servers are loaded without a GUI, we have one lone machine that has CENTOS because it is a vendor provided machine. Is there a difference between moving files between two Ubuntu machines versus two dis-similar Linux based machines?

If someone could help me wrap my mind around how file transfers work I would be most appreciative.

Also, I tried moving files between my Ubuntu desktop machine and the CENTOS machine using SFTP but kept getting a permission denied error. There are only two user accounts on the CENTOS machine root and one other user ID. I tried both and received the same error. Is it possible that SFTP is not even running on the CENTOS machine?

---

### Post by SeijiSensei on 2015-07-30
If the target has an SSH server, use scp for individual files or rsync for bulk transfers.
```
scp file user@remote:/path/to/destination
```

Rsync has a million options, but for simple transfers use
```
rsync -a source user@remote:/target
```
To get a list of the files being transferred use -av.  Rsync is picky about the syntax of the file definitions.  For instance, to move the directory "/home/me/documents" to "/archive" on the remote you would use:
```

cd /home/me
rsync -av documents remote:/archive

```
If you're not the owner of the destination location, you'll probably need to run these as root.  On Ubuntu you can use sudo; CentOS usually allows for root to have a password, so you'd have
```
sudo rsync -a source root@remote/target
```

Read the manual pages by typing "man scp" or "man rsync" to see all the gritty details.

---

### Post by Lars Noodén on 2015-07-30
+1 for rsync
It runs over SSH these days anyway.  

But if you are looking at running SFTP, what were the exact steps that you used to get the error?

---

### Post by ben152 on 2015-07-30
SCP was what I needed to make it happen. Unfortunately I still had to ask my co-worker who is the guru for help. Apparently the password authentication was disabled as well which was the other reason I couldn't file transfer or even SSH into the machine remotely. Maybe one of these days I'll stop struggling with trying to learn all of this. 

Also, as a side note the vendor hacked and modified Linux so that it is not by any means what would be standard if loaded from scratch. I have had numerous challenges with this vendors "load" of Linux which had made learning even more challenging because they have done things that are not the default or "normal" way Linux operates. 


Thanks for the help...

):P

---

