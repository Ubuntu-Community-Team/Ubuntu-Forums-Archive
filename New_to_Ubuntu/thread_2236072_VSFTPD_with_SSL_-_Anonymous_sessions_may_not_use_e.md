---
title: "VSFTPD with SSL - Anonymous sessions may not use encryption"
date: 2014-07-24
forum: New to Ubuntu
---

### Post by Cryonicblue on 2014-07-24
Hi. Since there are no official VSFTPD forums I hope I can get help by some kind person in this community.

I have set up vsftpd to use secure connections and when I try to login with FileZilla I just get:

```
Status:    Connecting to myipadressremoved:21...
Status:    Connection established, waiting for welcome message...
Response:    220 (vsFTPd 3.0.2)
Command:    AUTH TLS
Response:    234 Proceed with negotiation.
Status:    Initializing TLS...
Status:    Verifying certificate...
Command:    USER ftp
Status:    TLS/SSL connection established.
Response:    530 Anonymous sessions may not use encryption.
Error:    Could not connect to server
```

My vsftpd.conf:

```
listen=YES
anonymous_enable=NO
local_enable=YES
dirmessage_enable=YES
use_localtime=YES
xferlog_enable=NO
connect_from_port_20=YES
chroot_local_user=YES
secure_chroot_dir=/var/run/vsftpd/empty
pam_service_name=vsftpd
ssl_enable=YES
allow_anon_ssl=NO
force_local_data_ssl=YES
force_local_logins_ssl=YES
ssl_tlsv1=YES
ssl_sslv2=YES
ssl_sslv3=YES
require_ssl_reuse=NO
ssl_ciphers=HIGH
rsa_cert_file=/etc/vsftpd.pem
rsa_private_key_file=/etc/vsftpd.pem
pasv_max_port=65535
pasv_min_port=64000
```

Additional info:
* I have created the cert file.
* I have forward ports 20,21 on the router.
* I'm using Require explicit FTP over TLS as the encryption. -

---

