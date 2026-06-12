---
title: "need to do a repair after deleting a directory"
date: 2008-05-28
forum: New to Ubuntu
---

### Post by cambyth on 2008-05-28
I have deleted /etc/samba and now I get an error message. Is there some way I can repair it/reinstall it?
I googled and then did sudo apt-get -f install. I got:

The following packages were automatically installed and are no longer required:
  mplayer-skins openbsd-inetd
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up samba (3.0.28a-1ubuntu4) ...
 * Starting Samba daemons                                                [fail] 
invoke-rc.d: initscript samba, action "start" failed.
dpkg: error processing samba (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 samba
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by damis648 on 2008-05-28
Well I don't know for sure, but a reinstall of samba would be the first thing i would try.

---

### Post by quelx on 2008-05-28
have you tried (from the console) ```
sudo apt-get --purge remove samba
sudo apt-get autoremove
sudo apt-get install samba
```

---

### Post by cambyth on 2008-05-28
Thanks. 
I had already done an uninstall/install. 
I just tried the commands from quelx and I get the same error code.

Generating /etc/default/samba...
 * Starting Samba daemons                                                [fail] 
invoke-rc.d: initscript samba, action "start" failed.
dpkg: error processing samba (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 samba
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

