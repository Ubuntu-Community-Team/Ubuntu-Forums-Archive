---
title: "SSO Winbind while connected in an other domain"
date: 2013-04-18
forum: New to Ubuntu
---

### Post by Pured on 2013-04-18
Hi 


Here is the problem


I try to get work SSO with winbind
I have installed samba + kerberos + apache + winbind on two ubuntu server (ubuntu1 and ubuntu2).
I have an active directory on a windows server 2008 R2 (win)


I have a user 'toto' created in the active directory in the domain 'SSOTEST'


When i am logged on my station with the toto user in the SSOTEST domain, thats works good. I can join my two server without being prompt for login.


But if i am logged with an other user, in an other domain, which doesn't exists in the active directory i used, i get prompt when i try to join one of my ubuntu server.
Thats seems normal, so i enter the login 'toto' and it works good, but when i try to join the other ubuntu server, i get prompt again.


Is it normal? Is there a way to not being prompt again?


Here is the configuration of the different files, its the same for the two ubuntu server:


httpd.conf:


```
<Directory />
Options FollowSymLinks Multiviews Indexes
AllowOverride All
AuthName "Authentication"
NTLMAuth on
NTLMAuthHelper "/usr/bin/ntlm_auth --helper-protocol=squid-2.5-ntlmssp"
NTLMBasicAuthoritative on
AuthType NTLM
require valid-user
</Directory>

```



krb5.conf:


```
[libdefaults]
default_realm = SSOTEST.COM
# The following krb5.conf variables are only for MIT Kerberos.
krb4_config = /etc/krb.conf
krb4_realms = /etc/krb.realms
kdc_timesync = 1
ccache_type = 4
forwardable = true
proxiable = true
v4_instance_resolve = false
v4_name_convert = {
host = {
rcmd = host
ftp = ftp
}
plain = {
something = something-else
}
}
fcc-mit-ticketflags = true
[realms]
SSOTEST.COM = {
kdc = win.ssotest.com
}
[domain_realm]
.kerberos.server = SSOTEST.COM
[login]
krb4_convert = true
krb4_get_tickets = false

```



smb.conf:


```
[global]
workgroup = SSOTEST
realm = SSOTEST.COM
preferred master = no


log level = 3
log file = /var/log/samba.log
max log size = 50


security = ADS
encrypt passwords = yes


winbind use default domain = yes


winbind separator = +
idmap uid = 10000-20000
idmap gid = 10000-20000


[homes]
comment = Home Directories
valid users = %S
read only = No
browseable = No



```

nsswitch.conf:


```
passwd:  compat winbind  
group:  compat winbind  
shadow:  compat  
hosts:  files dns  
networks:  files  
protocols:  db files  
services:  db files  
ethers:  db files  
rpc:  db files

```



Thanks for the help!

---

