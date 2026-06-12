---
title: "Apache Help?"
date: 2008-04-29
forum: New to Ubuntu
---

### Post by freebullets on 2008-04-29
Hi, I'm really new to linux 8-[ 

What's the easiest way of uploading files from my Windows Vista machine to my Ubuntu machine?  

I tried to open "UBUNTU" in my network in vista, but it asks for a username and password.  I tried root and my username with the passwords, but I couldn't get in.

[SIZE="1"]Happy GTA IV Release Day![/SIZE]

---

### Post by lwvmobile on 2008-04-29
The publish files are generally in /var/www/ by default, but you can set up virtual hosts in the /etc/apache2/sites-available/ folder.

Check out this guide for configuring apache2, [https://help.ubuntu.com/8.04/serverguide/C/httpd.html]("https://help.ubuntu.com/8.04/serverguide/C/httpd.html")

---

### Post by freebullets on 2008-04-29
Thanks, I'll look through it.

---

### Post by Ek0nomik on 2008-04-29
> **freebullets said:**
> Hi, I'm really new to linux 8-[ and I want to know how to configure apache.

First off, I'm running Apache 2.2.4 and I'd like to upgrade to 2.2.8.  How would I do this?

Secondly, I managed to find where the apache configuration files were (/etc/bin/apache2/), but where is the folder where all the published files are?  Don't I have to do something with some kind of .htaccess file?


Out of curiosity, is there a reason why you want 2.2.8?  Specific change or bug fix you are seeking out?  The latest version of Apache2 in the Ubuntu Repository is 2.2.4, but you can probably compile 2.2.8 yourself or perhaps find a DEB file.

The published files are in /var/www

---

### Post by freebullets on 2008-04-29
I just like being "up-to-date" :P

On a side note, what's the easiest way of uploading files from my windows machine to my ubuntu machine?  Is it possible to network together windows (vista) and ubuntu?

---

### Post by Ek0nomik on 2008-04-29
> **freebullets said:**
> I just like being "up-to-date" :P

On a side note, what's the easiest way of uploading files from my windows machine to my ubuntu machine?  Is it possible to network together windows (vista) and ubuntu?

If you aren't actually seeking a specific problem with Apache, I'd just leave it at 2.2.4.  It isn't as if 2.2.4 is suddenly an unsupported release.  I have my web server running on 2.2.4.  :)

Sharing Files:  You could check out Samba and SSH.  I personally use SSH.

---

### Post by Ek0nomik on 2008-04-29
x

---

### Post by lwvmobile on 2008-04-29
Maybe you should just take a thorough look at the 8.04 server guide.

[https://help.ubuntu.com/8.04/serverguide/C/]("https://help.ubuntu.com/8.04/serverguide/C/")

Especially Samba, OpenSSH, Apache2, and what ever else strikes your fancy. Ubuntu Server can do anything any other server can do given the right application is available, you just gotta know how to do it, so check out the guide.

---

### Post by freebullets on 2008-04-29
I tried to open "UBUNTU" in my network in Vista, but it asks for a username and password.  I tried root and my username with the passwords, but I couldn't get in.

I couldn't really understand that guide. :S All I really need to do is be able to upload web files to my Ubuntu machine.  Even an FTP server would be sufficient.

---

### Post by Ek0nomik on 2008-04-29
> **freebullets said:**
> I tried to open "UBUNTU" in my network in Vista, but it asks for a username and password.  I tried root and my username with the passwords, but I couldn't get in.

I couldn't really understand that guide. :S All I really need to do is be able to upload web files to my Ubuntu machine.  Even an FTP server would be sufficient.

Try SSH.

On your SERVER Computer:

```
sudo apt-get install openssh-server
```

On your CLIENT Computer (Which is running Windows, correct?):

WinSCP (A graphical file transfer client (SSH) for Windows)
[http://winscp.net/download/winscp407setup.exe](http://winscp.net/download/winscp407setup.exe)

Then you connect using a username and password that you have on your server box.

Note:  Some files in /var/www (where your website files usually are) might be owned by root.  So, you can either make new folders which are privileged to your user name, or you can simply change the privileges of the existing folders.

---

### Post by freebullets on 2008-04-29
Thanks, I'll try that tomorrow.  Just got GTA IV, so I'm pretty much done for the night.  :popcorn:

---

### Post by Ek0nomik on 2008-04-29
> **freebullets said:**
> Thanks, I'll try that tomorrow.  Just got GTA IV, so I'm pretty much done for the night.  :popcorn:

Enjoy.  If you need more help just ask.

---

