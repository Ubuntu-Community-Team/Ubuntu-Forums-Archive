---
title: "pam_unix (sshd:auth): authentication failure issue"
date: 2014-01-15
forum: New to Ubuntu
---

### Post by dean.wheatley on 2014-01-15
Hi,

I have suddenly started to see the following entries in our auth.log file:
pam_unix(sshd:auth): authentication failure; logname= uid=0 tty=ssh ruser= rhost=192.168.1.22 user= xadmin
failed password for invalid user xadmin from 192.168.1.22 port 43319 ssh2

These happen when I try to ssh into our server, however I know the password is correct as I can login to the console using the same set of credentials locally and this only started yesterday.

If I do id xadmin from the console i get the following:

uid=1000(xadmin) gid=1000(xadmin) groups=1000(xadmin), 4(adm), 24(cdrom), 27(sudo), 30(dip), 46(plugin), 113(lpadmin), 114(sambashare)

I need to be able to putty into the server but am currently stuck for ideas of how to rectify this.

This is a virtual Apache server running on Ubuntu 12.04 LTS.

Drac

---

### Post by ian-weisser on 2014-01-16
Guess: Non-alphanumeric chars in the password?

---

### Post by dean.wheatley on 2014-01-16
There was a non alpha numeric chr in the password.  But that wasn't it, after much searching sifting and trial and error I discovered that the user group, xadmin, was no longer listed in the /etc/ssh/sshd_config file under allowed groups.  I am guessing here, but considering this started after a reboot I was only able to login previously because openssh hadn't completed the setup maybe and the reboot finished the job off.

Drac

---

