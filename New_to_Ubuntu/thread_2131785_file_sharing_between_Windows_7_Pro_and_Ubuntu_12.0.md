---
title: "file sharing between Windows 7 Pro and Ubuntu 12.04LTS"
date: 2013-04-02
forum: New to Ubuntu
---

### Post by alabamatoy on 2013-04-02
OK, so where do I begin.  I have tried RDP, and apparently you cant just copy and paste files as you can with Windows RDP client.  I have a share on the Windows box which I would really like to be able to access from Ubuntu.  "Files" shows a network browser, but all it seems to get from the Windows box is the name of the server ("Unable to mount...").  I can access the share from other Windows boxes on my NW, so I think my problem is on the Ubuntu side.  I attempted to install samba (sudo apt-get install samba4) and got: ```
ERROR: Invalid smb.conf
/var/lib/dpkg/info/samba4.postinst: 14: /var/lib/dpkg/info/samba4.postinst: /usr/share/samba/setoption.pl: Permission denied
dpkg: error processing samba4 (--configure):
 subprocess installed post-installation script returned error exit status 126
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Errors were encountered while processing:
 samba4
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

Any advice would be appreciated!

---

### Post by r.stiltskin on 2013-04-02
I think you should purge samba4 and then install samba instead.

---

### Post by alabamatoy on 2013-04-02
> **r.stiltskin said:**
> I think you should purge samba4 and then install samba instead.

purge?  How, "sudo apt-get uninstall samba4?"

---

### Post by mJayk on 2013-04-02
sudo apt-get remove --purge samba4

---

### Post by Paqman on 2013-04-02
You don't need to install the full Samba package just to access a Windows share, desktop Ubuntu includes the Samba client packages by default. You should just be able to navigate to it through the file browser.

Personally though I would [add an entry to /etc/fstab]("https://wiki.ubuntu.com/MountWindowsSharesPermanently") so that it automatically mounts at boot. Takes about five minutes to set up and then it just works nice and cleanly forever after.

---

### Post by alabamatoy on 2013-04-03
Thanks, Gang!  This seems to work.

---

