---
title: "Can anyone explain about FTP?"
date: 2008-05-12
forum: New to Ubuntu
---

### Post by eddie67 on 2008-05-12
I have installed the VSFTPD.
It is only me who will be FTP'ing to the server so I chose "stand-alone" in the config.

Now on my laptop I have Filezilla. When I try to connect to my server I try to use the user / passwd I used during installation of Ubuntu but I get "access denied". 

I suspect it has something to do with setting up a FTP-user or something ..

So how do I set up a FTP-user in Ubuntu 6.06 with all priveliges ?

Thanks.

Eddie.

---

### Post by jnorth on 2008-05-12
> **eddie67 said:**
> I have installed the VSFTPD.
It is only me who will be FTP'ing to the server so I chose "stand-alone" in the config.

Now on my laptop I have Filezilla. When I try to connect to my server I try to use the user / passwd I used during installation of Ubuntu but I get "access denied". 

I suspect it has something to do with setting up a FTP-user or something ..

So how do I set up a FTP-user in Ubuntu 6.06 with all priveliges ?

Thanks.

Eddie.

I usually use proftpd, but IIRC, vsftpd defaults to anonymous only.

Anyway, here's the easiest way to do this - edit the config file, and then restart vsftpd as below... (I used vi here, use whatever editor your are comfortable with, i.e. nano, etc
```
sudo vi /etc/vsftpd.conf
```Change ```
anonymous_enable=YES
``` to ```
anonymous_enable=NO
``` Change ```
#local_enable=YES
``` to ```
local_enable=YES
```
I'd _highly_ recommend that you limit the list of users and limit them to their home directories as follows:
Create an allowed users list file lik this ```
sudo vi /etc/vsftpd.chroot_list
``` and add the usernames of all you want to allow access to.
Then edit the vsftpd file again ```
sudo vi /etc/vsftpd.conf
``` and change ```
#chroot_list_enable=YES
``` to ```
chroot_list_enable=YES
```and ```
#chroot_list_file=/etc/vsftpd.chroot_list
``` to ```
chroot_list_file=/etc/vsftpd.chroot_list
```.
Lastly, if you want to allow your users to write to theirt directories, edit the vsftpd.conf file ```
sudo vi /etc/vsftpd.conf
``` and change ```
#chroot_local_user=YES
``` to ```
chroot_local_user=YES
```
Now restart vsftpd with ```
sudo /etc/init.d/vsftpd restart
```and test

HTH

---

