---
title: "Dropbox/Samba issues"
date: 2012-03-18
forum: New to Ubuntu
---

### Post by marineco on 2012-03-18
I installed Dropbox using [this tutorial]("http://ubuntuservergui.com/ubuntu-server-guide/install-dropbox-ubuntu-server") on my new server. We have been using dropbox as a backup system for some time now on our regular PCs. Now that I have set up a server, I want to access our files from it, instead of pulling from the oldest PC on my network, which is the only one I could get everything else to see. Plus the server has a faster connection. 
But I can't get my Samba to be willing to share that particular folder nicely. (/home/myname/dropbox)
I also tried to install Dropbox to one of my shares that does work, but for some reason I couldn't make that work either. 
Ideas?

---

### Post by Jest3r on 2012-03-24
Hello,

  This problem might be caused by the fact that by default the Dropbox directory permissions are setup so that only the user that installed dropbox is able to access the files and directories.

  You can fix this a number of ways, either change the dropbox directory so that *everyone* has access to it.

 ```
$ chmod 777 /home/myname/dropbox
```

**Or**

change your samba configuration ( /etc/samba/smb.conf ) to force everyone connecting to samba use the *myname* account

```

[dropbox]
    comment = dropbox share
    read only = no
    locking = yes
    path = /home/myname/Dropbox
    guest ok = yes
    writable = yes
    *force user = myname*

```

---

