---
title: "Ftp user doesn't have access"
date: 2013-11-17
forum: New to Ubuntu
---

### Post by kdermendzhiev on 2013-11-17
Hello, 

I have vsftpd server on ubuntu 12.04 and made to work with SFTP. When I create local user manual it's work, but when I made with shell script doesn't work.

this is my script: 

```
sudo useradd $DOMAIN_TEXT -p password -d "$CURRENT_ROOT" -s /bin/false`echo "$DOMAIN_TEXT:password" | sudo chpasswd`
chmod 0777 $CURRENT_ROOT
```

description:
```

ftp_script:x:1002:1002::/var/www/sites/mag/ftp_script:/bin/false
ftp_manual:x:1009:1009:ftp_manua,,,:/home/ftp_manual:/bin/bash

```

this is my vsftpd.conf
```

listen=YES
anonymous_enable=NO
local_enable=YES
write_enable=YES
dirmessage_enable=YES
use_localtime=YES
xferlog_enable=YES
connect_from_port_20=YES
secure_chroot_dir=/var/run/vsftpd/empty
pam_service_name=vsftpd
rsa_cert_file=/etc/ssl/private/vsftpd.pem
ssl_enable=YES
allow_anon_ssl=NO
force_local_data_ssl=YES
force_local_logins_ssl=YES
ssl_tlsv1=YES
ssl_sslv2=YES
ssl_sslv3=YES
hide_ids=YES
max_clients=5
local_root=/var/www/sites/magento/$USER

```

---

### Post by kdermendzhiev on 2013-11-18
If somebody know some suggestion I'm glad to hear.

---

### Post by BBQdave on 2013-11-18
From my **vsftpd** setup:


[LIST]
[*]By default vsftpd is not configured to allow anonymous download 
[*]By default vsftpd is configured to authenticate system users and allow them to download files. If you want users to be able to upload files, edit /etc/vsftpd.conf **write_enable=YES** 
[*]uncomment **local_enable=YES** 
[*]uncomment **write_enable=YES** 
[*]restart vsftpd 
[/LIST]

I access ftp accounts (users on the ftp server) with FileZilla. To access, you need to authenticate with user name and password. And this setup is behind multiple fire walls on a protected home network (only accessable from with in the home network).

---

### Post by kdermendzhiev on 2013-11-19
I did this BBQdave

---

### Post by steeldriver on 2013-11-19
The most obvious difference is that your manually created user has a valid login shell (/bin/bash) whereas the script created one uses /bin/false - are you sure /bin/false works for vsftpd? You may need to do something like create /bin/nologin as a symlink to /bin/false, set the ftp user's login shell to /bin/nologin, and then add /bin/nologin to the list of allowed shells at /etc/shells - or possibly use /usr/sbin/nologin (again adding it to /etc/shells if necessary) - I'm not sure which is regarded as better practice.

---

