---
title: "creating ftp users in ubuntu server (vsftpd)"
date: 2012-06-02
forum: New to Ubuntu
---

### Post by hookitup on 2012-06-02
hello i have a ubuntu server virtual machine for testing, i have install vsftpd so i can upload and download files to this machine via FTP, now i can access it anonymously but i do not know how to set it up where it ask for user authentication.

there is currently only one user profile on the server (mine) will i have to create more or what ? and how will i define the users home directory when they connect to the server?

---

### Post by hookitup on 2012-06-02
never mind figured it out. heres the info for thoes of you wondering how.

set up ftp service and users on ubuntu server

install ftp: ```
sudo apt-get install vsftpd
```check to see if it made directory /srv/ftp: ```
cd /srv/ftp
```if not then :```
sudo mkdir /srv/ftp
sudo usermod -d /srv/ftp ftp 
```then edit the ftp config file: ```
sudo nano /etc/vsftpd.conf
``` you want to edit the below to enable user authentication remove # from : local_enable=YES and
write_enable=YES

and also remove # from :chroot_list_enable=YES

then create the file to add users: ```
sudo touch /etc/vsftp.chroot_list
```then edit that file you just made: ```
sudo nano /etc/vsftp.chroot_list
```enter the name of the user(s) one per line
Example:/home/user1
/home/user2
        /home/user3 


save that file then

restart services : ```
service vsftp restart
```

---

### Post by Return Privacy on 2012-06-21
Hi Hookitup,
I found your post while trying to figure out how to configure vsftpd. I am new to using FTP in general. I got vsftpd working on Ubuntu 11.10. But, right now I can only upload to it from my other computer at home by logging in with the main Ubuntu user and password. ( I only have the main user admin account setup on Ubuntu). Can you please explain how I can setup vsftpd with 2 other user names and passwords? I only want to allow these 2 new users to be able to upload to vsftpd. They are actually 2 other computers on my home network. And, I only want them to be allowed to upload to the secondary drive on the ubuntu computer, which is called /Media/2ndDrive.
I don't want these 2 new users to see any other files or folders except their upload directory (/Media/2ndDrive)
I have read a lot, and I know it has to be done in the vsftpd.config file, but I don't understand what to add there?
Thank You

---

