---
title: "ftp server share mounted partition"
date: 2014-07-26
forum: New to Ubuntu
---

### Post by tubos2 on 2014-07-26
- I would like to setup a local ftp server to keep backups of my ip camera.

- The default folder seems to be the users account home folder.

- That would mean my IP camera can only write to folders in the home directory.


1) How can I get ftp access to a folder on /mnt/somedisk/somefolder ?

2) Are there disadvantages if i created a symbolic link in my homedir pointing to /mnt/somedisk/somefolder/ ?

---

### Post by mooreted on 2014-07-26
A lot of it depends on how your are setting up your FTP server. Here's one way:

[https://help.ubuntu.com/12.04/serverguide/ftp-server.html](https://help.ubuntu.com/12.04/serverguide/ftp-server.html)

Here's another way:

[https://filezilla-project.org/](https://filezilla-project.org/)

---

### Post by tubos2 on 2014-07-27
[SIZE=5][SIZE=4]How can I setup vsftpd to allow ftp access only to one folder ?[/SIZE]
[/SIZE]

---

