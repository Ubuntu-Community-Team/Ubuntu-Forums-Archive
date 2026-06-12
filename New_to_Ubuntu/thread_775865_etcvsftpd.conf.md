---
title: "/etc/vsftpd.conf"
date: 2008-04-30
forum: New to Ubuntu
---

### Post by ism. on 2008-04-30
Hi!I'm trying to set up FTP on another machine thats running Ubuntu server edition 7.10.  I'm supposed to edit my /etc/vsftpd.conf by going vi/nano /etc/vsftpd.conf.  When i go there, theres nothing in it.    Is the text in the qoute below supposed to be in there already or am i supposed to add that?  

Thanks in advanced,

-ism.




> listen=YES
anonymous_enable=YES
local_enable=YES
write_enable=YES
anon_upload_enable=YES
anon_mkdir_write_enable=YES
dirmessage_enable=YES
xferlog_enable=YES
connect_from_port_20=YES
chown_uploads=YES
chown_username=samurai
ftpd_banner=Welcome to blah FTP service.
secure_chroot_dir=/var/run/vsftpd
pam_service_name=vsftpd
rsa_cert_file=/etc/ssl/certs/vsftpd.pem
anon_root=/home/ftp

---

### Post by enigmaniac23 on 2008-04-30
go the the etc directory and do an ls to see if the file is there.

```
cd /etc
ls -l vsftp*
```

If you try to vi a file that doesn't exist, it will just open an empty file, so make sure the file is actually there first.

---

### Post by Monicker on 2008-04-30
> **enigmaniac23 said:**
> go the the etc directory and do an ls to see if the file is there.

```
cd /etc
ls -l vsftp*
```

If you try to vi a file that doesn't exist, it will just open an empty file, so make sure the file is actually there first.

You might also try these commands

```
locate vsftpd.conf
find / -name vsftpd.conf
```

---

### Post by ism. on 2008-04-30
When i use the ls -l vsftp* command it gives me 2 lines

> -rw-r--r-- 1 root root 5246 2006-12-13 10:42 vsftpd.conf 

-rw-r--r-- 1 root 60 2008-04-30 00:31 vsftpd.config

---

### Post by enigmaniac23 on 2008-04-30
hmmm.

based on what you put above, it doesn't look like vsftpd.conf would be empty.

what do you get if you do:
```
cat /etc/vsftpd.conf
```

---

### Post by ism. on 2008-04-30
> **Monicker said:**
> You might also try these commands

```
locate vsftpd.conf
find / -name vsftpd.conf
```


The first one told me no such file or directory the second gave me a huge list of permission denied

---

### Post by enigmaniac23 on 2008-04-30
try it with sudo 

```
sudo find / -name vsftpd.conf
```

This way you won't get all those permission denied.

---

### Post by ism. on 2008-04-30
> **enigmaniac23 said:**
> hmmm.

based on what you put above, it doesn't look like vsftpd.conf would be empty.

what do you get if you do:
```
cat /etc/vsftpd.conf
```

when i use cat it gives me this debian customization thing with alot of talking.  and when i use sudo find / -name vsftpd.conf it says 4 lines

usr/share/doc/vsftp/EXAMPLE/Virtual_users/vsftpd.con
usr/share/doc/vsftp/EXAMPLE/ internet_site_noinetd/vsftpd.config
usr/share/doc/vsftp/EXAMPLE/ internet_site/vsftpd.config
/etc/vsftpd.conf

thanks for the help so far

---

### Post by enigmaniac23 on 2008-04-30
Well, the cat command should just be showing you the file, so I'm not really sure about all that stuff you were seeing with regards to Debian customization.

how about using "more" to see what's in the file?   

```
more /etc/vsftpd.conf
```

---

### Post by ism. on 2008-04-30
When i use more it gives me alot of text and i believe its what i want to edit.  But if i go back and try it in vi it still gives me a blank

---

### Post by scorp123 on 2008-04-30
> **ism. said:**
> But if i go back and try it in vi it still gives me a blank Can you show us the precise command that you typed please?

---

### Post by ism. on 2008-04-30
sure! for the vi editor? I use vi etc/vsftpd.conf  .  I use that for other files and its worked

---

### Post by scorp123 on 2008-04-30
> **ism. said:**
> vi etc/vsftpd.conf And you really really typed it like that? The way you wrote it up there it would be wrong. A slash "/" is missing. But maybe you just mistyped it here in the posting? Also, you did use "sudo", right? e.g. what you really really typed was in fact
```
sudo vi /etc/vsftpd.conf
``` ... right?

---

### Post by ism. on 2008-04-30
> **scorp123 said:**
> And you really really typed it like that? The way you wrote it up there it would be wrong. A slash "/" is missing. But maybe you just mistyped it here in the posting? Also, you did use "sudo", right? e.g. what you really really typed was in fact
```
sudo vi /etc/vsftpd.conf
``` ... right?

yea that was a miss type but i got it all figured out!  thanks for all the help guys! Really did help

thanks again,

-ism.

---

