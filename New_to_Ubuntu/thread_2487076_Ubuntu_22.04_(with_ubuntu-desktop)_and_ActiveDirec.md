---
title: "Ubuntu 22.04 (with ubuntu-desktop) and ActiveDirectory Login Windows pam-auth-update"
date: 2023-05-22
forum: New to Ubuntu
---

### Post by szorzellacgt on 2023-05-22
Hi to All
I'm new with Ubuntu (or Debian)

my new project is to create a Server Ubuntu 22.04 and connect to it with ssh (then GUI) using users that are in Active Directory windows 2019.


I have followed few tutorials and forums but I'm not sure what happens.

1) I install ubuntu-desktop-minimal, everything ok, login by GUI (vmware console) or SSH-Putty, using local users (root or first user created during installation)
2) Install sssd sssd-tools realmd adcli libnss-sss libpam-sss samba-common-bin oddjob oddjob-mkhomedir packagekit  (or even only sssd-ad sssd-tools realmd adcli, what is better?)
3) Join domain ok

sudo realm  list

 type: kerberos
  realm-name:         THEDOMAIN
  domain-name:            THEDOMAIN
  configured: kerberos-member     
  server-software: active-directory
  client-software: sssd
  required-package: sssd-tools
  required-package: sssd
  required-package: libnss-sss
  required-package: libpam-sss
  required-package: adcli
  required-package: samba-common-bin
  login-formats: %U     <<<<<------   ( I have changed it so users don't need insert the domain....  so    user1 without   @THEDOMAIN)
  login-policy: allow-realm-logins


cat /etc/sssd/sssd.conf
modify True to False for use_fully_qualified_names

systemctl restart sssd.service

From prompt   I can run command      id user1    and the output is the info of user1 in the active direcotry of THEDOMAIN

EX.
root@server:# id user1
uid=271872634(user1) gid=271872637(sysgroup),271876379(ubuntuserver)



I have added the following line on /etc/pam.d/common-session 
"session optional pam_mkhomedir.so skel=/etc/skel umask=077"


From prompt I can run command    getnet password  user1

EX.
root@server:/# getent passwd user1user1:*:271872634:271872637:User1:/home/user1:/bin/bash






Now if I test to connect in SSH with user1 I have a failure, and I can still use local users in SSH and GUI


and here is the PROBLEM, if I run the command      pam-auth-update   
and decide to change with  "Create home directory on login" or "Unix authentication" ... or other...


The GUI disapears, I can reboot but I recieve a black screen, I see mouse on GUI but nothing
If I try to login in ssh I can use local users and domain users...

EX.
test@  <-IP->   's password:
Creating directory '/home/test'.


The programs included with the Ubuntu system are free software;
the exact distribution terms for each program are described in the
individual files in /usr/share/doc/*/copyright.


Ubuntu comes with ABSOLUTELY NO WARRANTY, to the extent permitted by
applicable law.


/usr/bin/xauth:  file /home/test/.Xauthority does not exist
test@server:~$





Thank you 
Every Help will be appreciate

Simone

---

### Post by MAFoElffen on 2023-05-22
> **szorzellacgt said:**
> I have added the following line on /etc/pam.d/common-session 
"session optional pam_mkhomedir.so skel=/etc/skel umask=077"

Is that a typo? Not positive, but shouldn't the umask for that be 0077?

Just going off of this:
RE: [https://ubuntuforums.org/showthread.php?t=1661329](https://ubuntuforums.org/showthread.php?t=1661329)

---

