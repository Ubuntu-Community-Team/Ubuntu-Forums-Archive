---
title: "Users removed by system update"
date: 2022-05-30
forum: New to Ubuntu
---

### Post by archycho on 2022-05-30
Hello friends , I am new to Ubuntu , I have installed a very clean system with very little packages .
Now I am facing a serious problem for the server system.

I installed the system 2022-05-21 with a default user myname which could login SSH and SUDO , 
after 5 days , I found I could not login the system via SSH , so I connected the console and recover the system by removing ROOT password .
After I logged to the system with recovered ROOT , I found the users are deleted when system apt update ran.

The log of the apt as follow:

```
Start-Date: 2022-05-26  09:11:41
Commandline: apt-get -qq install python -y
[COLOR=#000000][FONT=Menlo]Install: libpython2-stdlib:amd64 (2.7.17-2ubuntu4, automatic), python2.7-minimal:amd64 (2.7.18-1~20.04.1, automatic), python2.7:amd64 (2.7.18-1~20.04.1, automatic), python2:amd64 (2.7.17-2ubuntu4, automatic), python2-minimal:amd64 (2.7.17-2ubuntu4, automatic), python-is-python2:amd64 (2.7.17-4), libpython2.7-minimal:amd64 (2.7.18-1~20.04.1, automatic), libpython2.7-stdlib:amd64 (2.7.18-1~20.04.1, automatic)
End-Date: 2022-05-26  09:11:46
```

and the auth.log as follow:

```
/var/log/auth.log.1:May 26 09:12:23 webserver userdel[2579]: delete user 'myuser'
/var/log/auth.log.1:May 26 09:12:23 webserver userdel[2579]: delete 'myuser' from group 'adm'
/var/log/auth.log.1:May 26 09:12:23 webserver userdel[2579]: delete 'myuser' from group 'cdrom'
/var/log/auth.log.1:May 26 09:12:23 webserver userdel[2579]: delete 'myuser' from group 'sudo'
/var/log/auth.log.1:May 26 09:12:23 webserver userdel[2579]: delete 'myuser' from group 'dip'
/var/log/auth.log.1:May 26 09:12:23 webserver userdel[2579]: delete 'myuser' from group 'plugdev'
/var/log/auth.log.1:May 26 09:12:23 webserver userdel[2579]: delete 'myuser' from group 'lxd'
/var/log/auth.log.1:May 26 09:12:23 webserver userdel[2579]: removed group 'myuser' owned by 'myuser'
/var/log/auth.log.1:May 26 09:12:23 webserver userdel[2579]: removed shadow group 'myuser' owned by 'myuser'
/var/log/auth.log.1:May 26 09:12:23 webserver userdel[2579]: delete 'myuser' from shadow group 'adm'
/var/log/auth.log.1:May 26 09:12:23 webserver userdel[2579]: delete 'myuser' from shadow group 'cdrom'
/var/log/auth.log.1:May 26 09:12:23 webserver userdel[2579]: delete 'myuser' from shadow group 'sudo'
/var/log/auth.log.1:May 26 09:12:23 webserver userdel[2579]: delete 'myuser' from shadow group 'dip'
/var/log/auth.log.1:May 26 09:12:23 webserver userdel[2579]: delete 'myuser' from shadow group 'plugdev'
/var/log/auth.log.1:May 26 09:12:23 webserver userdel[2579]: delete 'myuser' from shadow group 'lxd'
```

I have lost system control serval times for Ubuntu with username rather than ROOT , 
am I have any mis-understanding of Ubuntu systems ? 
Was it cause by my mistakes ? Thanks for any advise.

---

### Post by oldfred on 2022-05-30
You do not create a root user but use sudo when administrative access is required. Other distributions may use a root account but expect user to log out of root when done with admin activities.
Forum rules on root vs. sudo
[http://ubuntuforums.org/showthread.php?t=1486138](http://ubuntuforums.org/showthread.php?t=1486138)
[http://xkcd.com/149/](http://xkcd.com/149/)
[https://help.ubuntu.com/community/WikiGuide](https://help.ubuntu.com/community/WikiGuide)

Why python2?
That is obsolete and now python3 is the standard. Very few & obsolete applications still use python2, but may lead to other issues.
And you never replace default python with another. You can install other python3 versions, but default must remain same version as originally installed or you break the system.

---

