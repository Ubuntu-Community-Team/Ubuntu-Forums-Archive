---
title: "[SOLVED] vsftpd starts automatically on startup"
date: 2008-06-22
forum: New to Ubuntu
---

### Post by harsh_ on 2008-06-22
My vsftpd starts automaatically on system start up/.... the .conf file is
# Put in /etc/vsftpd.conf
# Don't forget to change samurai into your local username
listen=YES
anonymous_enable=YES
local_enable=YES
write_enable=NO
anon_upload_enable=NO
anon_mkdir_write_enable=NO
dirmessage_enable=YES
xferlog_enable=YES
connect_from_port_20=YES
chown_uploads=YES
chown_username=harsh
ftpd_banner=Welcome to HK's FTP service.
secure_chroot_dir=/var/run/vsftpd
pam_service_name=vsftpd
rsa_cert_file=/etc/ssl/certs/vsftpd.pem
anon_root=/home/ftp/



I dont want to start it as the system starts but start by the command
sudo /etc/init.d/vsftpd start

Please help

---

### Post by dje on 2008-06-22
System >> Administration >> Services

Unlock with your admin password and then untick
```
FTP server (vsftpd)
```
or something like that

hope that helps,
dje

---

### Post by harsh_ on 2008-06-22
I moved the file from init.d to /etc...as init.d contains the files to be executed on startup.....



SELF SOLVING THE PROBLEM

---

