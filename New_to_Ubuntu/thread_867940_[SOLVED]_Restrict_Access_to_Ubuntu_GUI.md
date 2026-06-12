---
title: "[SOLVED] Restrict Access to Ubuntu GUI"
date: 2008-07-23
forum: New to Ubuntu
---

### Post by flygy6 on 2008-07-23
Hi,

I am running a file server that runs pure-ftpd.  It also provides access via rsync tunneled through ssh and sftp.  I want to set up  users of the file server so that they have access to ssh (in order to use rsync) (I use rssh in chroot jail for a shell) and they also have access to the ftp server, but I want to restrict these users' access to the local system, both through the terminals (tty1 ...) and through the gui.  I am using hardy heron ubuntu.  I successfully restricted access to the terminals using /etc/security/access.conf, but I cannot restrict access to the gui for any user.  Please help.
Thank you,
flygy6

---

### Post by apswartz on 2008-07-23
I'm not sure I understand. If you only have one gui installed, how can they access through any other? (or do you have more than one installed?)

---

### Post by freak42 on 2008-07-23
Hi

under System-> Administration -> Login Window -> Security you can change various settings related to login and security, maybe these are of help.
(I think these settings are for gui-logins only? anyone?)

---

### Post by flygy6 on 2008-07-25
Thanx everyone for replying, but I found the solution I was looking for.  I setup user-specific login settings in /etc/security/access.conf.  However I needed to enable the various programs such as pure-ftpd, sshd, and gdm to use these user-specific login settings.  To do this I needed to go into /etc/pam.d to append the following line:
account required pam_access.so
to every program that I wanted to use access.conf.
I found the solution at:
[http://www.cyberciti.biz/tips/openssh-root-user-account-restriction-revisited.html](http://www.cyberciti.biz/tips/openssh-root-user-account-restriction-revisited.html)
Thanx again everyone for your help,
flygy6

---

### Post by cariboo on 2008-07-25
If you don't want users to use the gui on your server get, get rid of it. There are no server specific application on the desk top. I would suggest installing webmin to administer your server. Webmin is a web based administration suite. Have a look at Webmin here:

[http://www.webmin.com/](http://www.webmin.com/)

and there is a howto here:

[http://ubuntuforums.org/showthread.php?t=7507](http://ubuntuforums.org/showthread.php?t=7507)

Jim

---

