---
title: "Connection error: Software caused connection abort"
date: 2014-05-01
forum: New to Ubuntu
---

### Post by simon35 on 2014-05-01
I've seen several posts about keepalives solving this problem, but for me they are not. 

My exact scenario is as follows:

Several weeks ago I could FTP to my server without any problems with all of my individual ftp accounts. They were set up with the internal-sftp shell set for each one and the home directory set to each of the websites in question. I no longer can connect with any of them with the error "Connection error: Software caused connection abort". I removed every FTP account so I could set them all up again in case there was simply a problem with settings somewhere. (I like the nuke-the-site-from-orbit approach)

I created a new account using the following line:
sudo useradd -g webusers -d /path/to/web/site username

and set a password. and didn't change the shell so I could SSH in using PuTTY.

That account also gets the error "Connection error: Software caused connection abort" through PuTTY. In-fact that error appears on all FTP clients and PuTTY.

HOWEVER:

I can ssh in still using my main sudoer account and password. Which also means I can sftp in using any of my FTP clients. However this is FAR from ideal and that account does not have the correct permissions to modify all the individual websites.

Does anyone have any ideas as to what the hell is going on here?

Thanks.

---

### Post by sandyd on 2014-05-01
Have you checked the auth logs, particularly
```

/var/log/auth.log
```
after a login error?

You can check by running
```

sudo tail -n10 /var/log/auth.log
```

---

### Post by steeldriver on 2014-05-01
I think we'd really need to see your /etc/ssh/sshd_config file - the most likely thing I can think is that your new user's primary group (webusers) is the same as that of the original FTP accounts and is matching a chroot rule in your configuration - which then either prevents normal PAM login or requires root ownership of the user's home dir / chroot

---

