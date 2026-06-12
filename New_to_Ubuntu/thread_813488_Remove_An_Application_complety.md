---
title: "Remove An Application complety"
date: 2008-05-30
forum: New to Ubuntu
---

### Post by markbusu on 2008-05-30
Hi,

I installed:

```
aptitude install courier-base courier-authdaemon courier-authlib-mysql courier-imap courier-imap-ssl courier-ssl
```

However, i made some screw ups in the config... and deleted the /etc/courier config files..

However, now when i try to install it... it is looking for those configuration files:

```
Do you want to continue [Y/n]? Y
(Reading database ... 47115 files and directories currently installed.)
Removing courier-imap ...
 * ERR: /usr/sbin/couriertcpd missing
invoke-rc.d: initscript courier-imap, action "stop" failed.
dpkg: error processing courier-imap (--purge):
 subprocess pre-removal script returned error exit status 1
 * ERR: /usr/sbin/couriertcpd missing
invoke-rc.d: initscript courier-imap, action "start" failed.
dpkg: error while cleaning up:
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 courier-imap
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

Is there any way to tell apt-get to install from scratch?? to re create the configuration files once again?

thanks!

---

### Post by damis648 on 2008-05-30
us```
e
sudo apt-get uninstall --purge appname
```
and just replace appname with the name of the app. That should do it.

---

### Post by markbusu on 2008-05-30
I tried purging already... however get the same problem :S

---

### Post by iaculallad on 2008-05-30
Edit the post-installation file:

```
sudo gedit /var/lib/dpkg/info/courier-imap.postinst
```

then try adding **exit 1** at the top of your opened file and save.

Then purge courier-imap

```
sudo apt-get remove --purge courier-imap
```

and reinstall courier-imap again

```
apt-get install courier-imap
```

Hope this could work in your case.

---

### Post by markbusu on 2008-05-30
Came across that one... however still no luck... gonna try compile it a purge it...

Thanks!

---

