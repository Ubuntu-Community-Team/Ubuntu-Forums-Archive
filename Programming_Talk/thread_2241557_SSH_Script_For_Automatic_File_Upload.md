---
title: "SSH Script For Automatic File Upload"
date: 2014-08-26
forum: Programming Talk
---

### Post by craigw0w on 2014-08-26
Hi guys!

I hope this hasn't been asked too many times but,

Would someone be able to help me write or point me in the direction to some helpful tutorials in order to write a script to transfer a file directly to a server via SSH from a linux based computer.
The script should do as following:

1. Open the secure shell
2. Auto login
3. Copy the file to the server/address
4. Disconnect ssh
5. Wait 15minutes 
6. repeat (go to step 1)


Any help is greatly appreciated. 

Regards

Craig

---

### Post by Lars Noodén on 2014-08-27
[sftp](http://manpages.ubuntu.com/manpages/trusty/en/man1/sftp.1.html) has a batch mode that can be used for automated file transfers, when used in conjunction with keys or certificates.  

The first step though is getting the automated login with ssh with keys or certificates.  Probably an ed25519 key is better these days than an RSA key.

---

### Post by SeijiSensei on 2014-08-27
scp is even easier to use in these cases than sftp.  Use shared keys to authenticate, then just run the command:
```
scp /path/to/local.file server:/path/to/remote/destination
```

---

### Post by zirby on 2014-09-08
For my part, I prefer Rsync.
Here is a quite good tuto:
[https://www.digitalocean.com/community/tutorials/how-to-use-rsync-to-sync-local-and-remote-directories-on-a-vps](https://www.digitalocean.com/community/tutorials/how-to-use-rsync-to-sync-local-and-remote-directories-on-a-vps)

---

