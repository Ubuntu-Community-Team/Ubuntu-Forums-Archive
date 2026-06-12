---
title: "VSFTPD user level configuration IE issue"
date: 2012-12-25
forum: New to Ubuntu
---

### Post by GoldTipu on 2012-12-25
- VSFTPD Configuration . 
I am little confused as i am new . 
i have just configured ftp on server. i have default user login behavior .

- Login via SSH >FTP user landed in home directory which is fine ..


ftp> ls
200 PORT command successful. Consider using PASV.
150 Here comes the directory listing.
drwxr-xr-x    2 1000     1000         4096 Dec 24 18:23 Desktop
drwxr-xr-x    2 1000     1000         4096 Dec 24 18:23 Documents
drwxr-xr-x    2 1000     1000         4096 Dec 24 18:23 Downloads
drwxr-xr-x    2 1000     1000         4096 Dec 24 18:23 Music
drwxr-xr-x    2 1000     1000         4096 Dec 24 18:23 Pictures
drwxr-xr-x    2 1000     1000         4096 Dec 24 18:23 Public
drwxr-xr-x    2 1000     1000         4096 Dec 24 18:23 Templates
drwxr-xr-x    2 1000     1000         4096 Dec 24 18:23 Videos
-rw-r--r--    1 1000     1000            0 Dec 25 06:34 examples.desktop

- Now if i use Google Chrome That's Works Fine (See Screen shot ) 
- The issue is with IE when i use IE the user landed in Root and have full access to the whole drive . which is bad . 




[IMG]http://postimage.org/image/jaivea26b/[/IMG]

Image posted here if not showing 
[http://postimage.org/image/jaivea26b/](http://postimage.org/image/jaivea26b/)


My issue is . I want one single user just for FTP and have no access to any other drive he can only upload / download to a single folder . 

any help please to achieve this as i am new . 
Kind Regards
GoldTipu

---

### Post by GoldTipu on 2012-12-29
> **GoldTipu said:**
> - VSFTPD Configuration . 
I am little confused as i am new . 
i have just configured ftp on server. i have default user login behavior .

- Login via SSH >FTP user landed in home directory which is fine ..


ftp> ls
200 PORT command successful. Consider using PASV.
150 Here comes the directory listing.
drwxr-xr-x    2 1000     1000         4096 Dec 24 18:23 Desktop
drwxr-xr-x    2 1000     1000         4096 Dec 24 18:23 Documents
drwxr-xr-x    2 1000     1000         4096 Dec 24 18:23 Downloads
drwxr-xr-x    2 1000     1000         4096 Dec 24 18:23 Music
drwxr-xr-x    2 1000     1000         4096 Dec 24 18:23 Pictures
drwxr-xr-x    2 1000     1000         4096 Dec 24 18:23 Public
drwxr-xr-x    2 1000     1000         4096 Dec 24 18:23 Templates
drwxr-xr-x    2 1000     1000         4096 Dec 24 18:23 Videos
-rw-r--r--    1 1000     1000            0 Dec 25 06:34 examples.desktop

- Now if i use Google Chrome That's Works Fine (See Screen shot ) 
- The issue is with IE when i use IE the user landed in Root and have full access to the whole drive . which is bad . 




[IMG]http://postimage.org/image/jaivea26b/[/IMG]

Image posted here if not showing 
[http://postimage.org/image/jaivea26b/](http://postimage.org/image/jaivea26b/)


My issue is . I want one single user just for FTP and have no access to any other drive he can only upload / download to a single folder . 

any help please to achieve this as i am new . 
Kind Regards
GoldTipu

Bump !!!

---

### Post by squakie on 2012-12-29
Can you actually access the contents in those folders you don't want to share?

---

### Post by GoldTipu on 2012-12-30
> **squakie said:**
> Can you actually access the contents in those folders you don't want to share?

Thank you for the reply . My issue resolved by doing this . 

#enabled in vsftpd 
chroot_local_user=YES

#then i have done following for each user i required to hvee access. now everything is ok . 

sudo chmod a-w /home/user

Thank you for asking.

---

