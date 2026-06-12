---
title: "XAMPP : error accessing public_html folder on user account"
date: 2008-11-24
forum: New to Ubuntu
---

### Post by you123456 on 2008-11-24
hi all, 
I have successfully installed Ubuntu 8.10, after which i installed XAMPP version 1.6.8a

I followed the instructions on [http://www.apachefriends.org/en/xampp-linux.html](http://www.apachefriends.org/en/xampp-linux.html) and installed xampp successfully.

I would like to be able to publish on a user acccount. I used the following commands:

on terminal :
cd ~
mkdir public_html
sudo ln -s public_html /opt/lampp/htdocs/$USER

After which , i should be able to access my website(s) at [http://localhost/user](http://localhost/user)

But i recieved an error message : You don't have permission to access /eugene on this server

May i know what is wrong? I was logged in as my user account, and installed XAMPP into /opt

Any idea how do i fix this?

BEst Regards,
Eugene

---

### Post by Xiong Chiamiov on 2008-11-27
Most likely, it's a permissions issue.  I'd recommend creating the folder in /opt/lampp/htdocs and the symlink in your home dir, personally.

Also, please note that XAMPP is meant for development, not deployment.  There are inherent security risks in it, so if you actually want to display html for the world to see, you should use a proper LAMP setup.

---

