---
title: "Please help with XAMPP ASAP."
date: 2008-07-15
forum: New to Ubuntu
---

### Post by ImThatNerd on 2008-07-15
I really need to get XAMPP working again and having some problems. I had XAMPP installed for awhile and it was working perfectly. Then yesterday it seemed to stop working. When I started it through the control panel or manually it said that ProFTPD would not start and I had another FTP daemon is already running. So I rebooted my computer and same thing. I uninstalled then reinstalled XAMPP and same thing is going on. How can I fix this? It is urgent.

---

### Post by ImThatNerd on 2008-07-15
Anyone? I really need this ProFTPD to start.

---

### Post by Dr Small on 2008-07-15
Have you tried:
```
sudo /opt/lampp/lampp startftp
```

??

---

### Post by ImThatNerd on 2008-07-16
Like I said, whether I start it manually (terminal) or through the control panel it doesn't work.

```
ryan@ryan-desktop:~$ sudo /opt/lampp/lampp startftp
[sudo] password for ryan: 
XAMPP: Another FTP daemon is already running.
ryan@ryan-desktop:~$ 







```

But when I try to stop it it says:

```
ryan@ryan-desktop:~$ sudo /opt/lampp/lampp stop
Stopping XAMPP for Linux 1.6.7...
XAMPP: Stopping Apache with SSL...
XAMPP: Stopping MySQL...
XAMPP: XAMPP-ProFTPD is not running.
XAMPP stopped.
ryan@ryan-desktop:~$ 
ryan@ryan-desktop:~$ 
ryan@ryan-desktop:~$ 















```

---

### Post by ImThatNerd on 2008-07-16
Bump.

---

### Post by ImThatNerd on 2008-07-16
bump. =/

---

### Post by silverglade00 on 2008-07-16
type in
sudo ps aux | grep ftp

that will get you the name of the running ftp server

then sudo /etc/init.d/ftpserver_from_above stop

---

### Post by ImThatNerd on 2008-07-16
Oh man, thank you so much!

Do you know why it was doing this all of a sudden? And wouldnt stop any other way?

I started it and now when I go to localhost.com or even localhost.com/ryan it doesn't work.

---

### Post by silverglade00 on 2008-07-16
Try it without the ".com"..  

[http://localhost](http://localhost)

or

[http://127.0.0.1](http://127.0.0.1)

This should get you the "It Works!" page.

---

