---
title: "Ubuntu Radius AD integration"
date: 2019-08-26
forum: New to Ubuntu
---

### Post by skhan76 on 2019-08-26
Hi All,

I am new to Ubuntu and I am looking for some help around using FreeRadius on Ubuntu 18.04 (AWS AMI) to authenticate wireless uses against AD using PEAP authentication. I can get radius to work with local database but I am struggling to get Radius integrated to AD. I think I need to have this working in order for AD auth to work?

[https://help.ubuntu.com/community/ActiveDirectoryWinbindHowto](https://help.ubuntu.com/community/ActiveDirectoryWinbindHowto)

I have following the instructions and I am having issues sorting out permissions for sssd.conf as I get following error. If anyone has any idea it will be greately appreciated

```
ubuntu@ip-10-0-1-195:/etc$ sudo systemctl restart sssd.service
Job for sssd.service failed because the control process exited with error code.
See "systemctl status sssd.service" and "journalctl -xe" for details.
ubuntu@ip-10-0-1-195:/etc$ systemctl status sssd.service
&#9679; sssd.service - System Security Services Daemon
   Loaded: loaded (/lib/systemd/system/sssd.service; enabled; vendor preset: enabled)
   Active: failed (Result: exit-code) since Mon 2019-08-26 15:01:26 UTC; 17s ago
  Process: 26497 ExecStart=/usr/sbin/sssd -i ${DEBUG_LOGGER} (code=exited, status=4)
 Main PID: 26497 (code=exited, status=4)


Aug 26 15:01:26 ip-10-0-1-195 systemd[1]: Starting System Security Services Daemon...
Aug 26 15:01:26 ip-10-0-1-195 sssd[26497]: Cannot read config file /etc/sssd/sssd.conf. Please check that the file is accessible only by the owner and owned by root.root.
Aug 26 15:01:26 ip-10-0-1-195 systemd[1]: sssd.service: Main process exited, code=exited, status=4/NOPERMISSION
Aug 26 15:01:26 ip-10-0-1-195 systemd[1]: sssd.service: Failed with result 'exit-code'.
Aug 26 15:01:26 ip-10-0-1-195 systemd[1]: Failed to start System Security Services Daemon.

```
I have noticed that I am unable to change permissions for root

```
ubuntu@ip-10-0-1-195:/etc$ sudo chmod 600 /etc/sssd/sssd.conf
ubuntu@ip-10-0-1-195:/etc$ sudo chown root:root /etc/sssd/sssd.conf


ubuntu@ip-10-0-1-195:/etc$ ls -l /etc/sssd/sssd.conf
-rw------- 1 root root 700 Aug 26 14:19 /etc/sssd/sssd.conf

```

---

### Post by #&amp;thj^% on 2019-08-26
I mean no harm here but why do you change fonts and colors? You'll get more help with the default settings, And the use of [Code Tags]("https://ubuntuforums.org/misc.php?do=bbcode#code")
Welcome to forums though. :)
Thanks to deadflowr for the change. ;)

---

### Post by TheFu on 2019-08-26
> **skhan76 said:**
>  
I have noticed that I am unable to change permissions for root

```
ubuntu@ip-10-0-1-195:/etc$ sudo chmod 600 /etc/sssd/sssd.conf
ubuntu@ip-10-0-1-195:/etc$ sudo chown root:root /etc/sssd/sssd.conf


ubuntu@ip-10-0-1-195:/etc$ ls -l /etc/sssd/sssd.conf
-rw------- 1 root root 700 Aug 26 14:19 /etc/sssd/sssd.conf

```

I don't understand.  If you run those chown and chmod commands, the permissions shown ARE what you'd get.
I can't help with AD anything, sorry.

---

### Post by #&amp;thj^% on 2019-08-26
See if any of this helps: [https://draculaservers.com/tutorials/freeradius-ubuntu-18-04-mysql/](https://draculaservers.com/tutorials/freeradius-ubuntu-18-04-mysql/)

---

