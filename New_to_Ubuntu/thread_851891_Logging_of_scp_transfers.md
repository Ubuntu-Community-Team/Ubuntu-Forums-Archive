---
title: "Logging of scp transfers?"
date: 2008-07-07
forum: New to Ubuntu
---

### Post by peterlauri on 2008-07-07
Hello,

I have tried to find out where to be able to find any logging of scp transfers. I scp'd a file to my machine, but cannot find any trace of the file in any log file. The only thing that shows the activity is auth.log for the ssh authentication.

If this is not default, is it configurable somehow?

Thanks,
Peter

---

### Post by spiderbatdad on 2008-07-07
[http://ubuntuforums.org/archive/index.php/t-241188.html](http://ubuntuforums.org/archive/index.php/t-241188.html)

```
$ mkdir /tmp/openssh; cd /tmp/openssh

here are the commands i used .. paste them into the terminal or create a bash script.

#!/bin/bash
# ================================================== ===========
# begin of script

# uncomment the following line if you dont have these installed
# sudo aptitude install patch patchutils fakeroot

# remove existing package
sudo aptitude remove openssh-server

# purge configuration files
sudo dpkg --purge openssh-server

# build dependancy packages needed to compile source
sudo apt-get build-dep openssh-server

# verify no broken dependancies
sudo aptitude update
sudo aptitude upgrade

# download source packages
apt-get source openssh-server

# download patch, 'buntu currently installs openssh-4.2p1 so i use the
# appropriate patch, change accordingly if you use a different version
wget sftplogging.sourceforge.net/download/v1.5/openssh-4.2p1.sftplogging-v1.5.patch

# patch source
patch -p0 < openssh-4.2p1.sftplogging-v1.5.patch

# build package
fakeroot apt-get source -b openssh-server

# install package
sudo dpkg -i ./*.deb

# end of script
# ================================================== =========

now verify sshd is running

$ sudo ps aux | grep sshd
root 1543 0.0 0.4 4756 1072 ? Ss 21:00 0:00 /usr/sbin/sshd

verify you can connect to sshd
$ ssh localhost

(if you had sshd running before and the daemon is is running now you'll notice here warnings about how RSA keys have changed .. purge the ~/.ssh/ directory)

edit the sshd_config file (you might want to look into the sshd_config manpage for directives to match your requirements, also refer to http://sftplogging.sourceforge.net/docs/installation.html)
$ sudo vi /etc/ssh/sshd_config

once you've saved changes, restart sshd
$ sudo /etc/init.d/ssh force-reload

if all went well, you're pretty much set now. Sftp activities are loggged to /var/log/auth.log under the sftp-server process name.

don't forget to cleanup the temporary directory you were working in..

```

---

### Post by peterlauri on 2008-07-07
As I understand it, this is sftp, not scp, right? I just need it fo scp.

---

