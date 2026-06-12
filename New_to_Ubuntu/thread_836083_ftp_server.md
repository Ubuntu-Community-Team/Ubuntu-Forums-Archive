---
title: "ftp server"
date: 2008-06-21
forum: New to Ubuntu
---

### Post by _TED_ on 2008-06-21
I just downloaded and installed vsftpd, but I can't really make it work...

my configuration file is:


listen=YES
listen_ipv6=NO


local_enable=YES

anonymous_enable=YES
no_anon_password=YES
ftp_username=ftp
anon_root=/ftp/anon
anon_mkdir_write_enable=YES
anon_upload_enable=YES
anon_world_readable_only=YES
allow_anon_ssl=YES

local_root=/ftp

dirlist_enable=YES

log_ftp_protocol=YES

write_enable=NO

file_open_mode=0777




problems:
[SIZE="1"]1) It takes much time to connect as anonymous (!!)[/SIZE] - It must be from my windows... Ignore it
2) it doesn't allow me to connect as another user
3) I can't upload anything (as anonymous)
4) I can't restart vsftpd (!!!)

I need it to:
accept anonymous connections, and redirect them to /ftp/anon
accept connections from other users, and redirect them to /ftp
accept one user named user and redirect him to /var/www
all will have read/write access...

how can I do this? ^_^

---

### Post by superprash2003 on 2008-06-21
i'd say you better try proftpd server .. and also install gproftpd which is the GUI for proftpd. there you can setup your ftp server using a GUI which is pretty easy and doesnt require you to edit or configure any file..

---

### Post by _TED_ on 2008-06-21
I don't really have a gui...

I tried proftpd and pure-ftp too, but I did't manage to do something... :(

---

### Post by Nythain on 2008-06-21
i dont know how you managed to NOT do something/anything with proftpd, its quite possibly the most popular and well documented ftp server at the moment... im not familiar with any of the others, but if you wanted to give proftpd another try, google "<ubuntu version here> perfect server setup", there's a guide on howto forge that covers setting up ever aspect of a server, including proftpd, that gets rewritten for almost every release of ubuntu... im at work so i dont have the link readily available, but it should be one of the first hits you get

---

### Post by _TED_ on 2008-06-21
could you help me with that a little?

what sould I do, after installation?

I have the foldgers:
```

            ftp
           /   \
        anon   www
          |     |
      upload   site1

```
so, I need anonymous to be redirected in anon, 
one user to be redirected in ftp
one other user, to be redirected in www

all users sould have 777 access to their foldgers

so?

---

### Post by imon9 on 2008-06-21
in proftpd and pure-ftpd, you get to set the "virtual directory" of each folder u want certain user to access...

so, for the folder "anon", allow all user (thus anonymous user will be able to access it)

for one user eg: user1, make a virtual directory for folder "FTP"

for the another user eg: user1, make a virtual directory for foder "www"
...

if you need specific instruction, post here and ask again...
but i am not answering for vsftp

my personal favourite is pure-ftpd..so i'm willing to guide you step by step for pure-ftpd

---

### Post by _TED_ on 2008-06-21
why everyone is against vsftpd?? anyway, you sould know better...

What sould I do to configure pure-ftp?

---

### Post by imon9 on 2008-06-21
INSTALL PURE_FTPD
(1) install pure-ftpd
apt-get install pure-ftpd-common pure-ftpd

(2) add group that correspond to pure-ftpd
sudo groupadd pure-ftp

(3) add user to the group
sudo useradd -g pure-ftp -d /dev/null -s /etc pure-users

(4) add virtual users to FTP server (this is the one needed for login later)

sudo pure-pw useradd test-user1 -u pure-users -g pure-ftp -d  /FTP

sudo pure-pw useradd test-user2 -u pure-users -g pure-ftp -d  /FTP/www

(5) IMPORTANT!! save the virtual users database
sudo pure-pw mkdb

(6) IMPORTANT! tweak pureftpd to use this new database. 
(else you won't be able to log-in even after u added the user)

cd /etc/pure-ftpd/auth
sudo ln -s ../conf/PureDB 50pure

this will allow pure-ftpd to read the user database you've created

(7) Tweak pure-ftpd settings like ports, etc.
(7.1) to change the port:
sudo nano /etc/pure-ftpd/conf/Bind
in the empty file, type in "*,9000" (without the " ") this is the IP and port number, then save the file

..about the anonymous part, i will post later

---

### Post by angel6700 on 2009-05-08
Hello, I know  this a one year old post, so sorry about that. But The last post says in the last line:

> ..about the anonymous part, i will post later 

Do imon9 or someone else know how to add anonymous functionality to pureftp after adding virtual users??


Thanks a lot.

---

