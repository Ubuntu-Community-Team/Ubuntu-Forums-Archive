---
title: "How to configure firewall ports in 11.10"
date: 2012-03-31
forum: New to Ubuntu
---

### Post by shotgun sam on 2012-03-31
The problem is that they're thousands of different port numbers which are the important ones to configure and is there a way to do this automatically?

---

### Post by lovinglinux on 2012-03-31
The simplest way is to install gufw, set it to deny incoming, allow outgoing. If you need to allow incoming connections, for example to use a torrent client, then make a rule for it.

Keep in mind that you don't need to run gufw once you configure it.

Recommended reading 

[http://ubuntuforums.org/showthread.php?t=510812](http://ubuntuforums.org/showthread.php?t=510812)

[http://ubuntuforums.org/showthread.php?t=1871177](http://ubuntuforums.org/showthread.php?t=1871177)

---

### Post by Frogs Hair on 2012-03-31
You can install Firewall Configuration from the software and add rules if needed but you have to have some idea of your purpose . The default settings should be fine for every day use.

If you would like to use the terminal that is also possible . You can find instruction for specific rules by searching. Here are some basic commands , but you need to know specific ports and ip addresses. See the link also. Figure out what you would like to do and do some reading an research. 

[https://help.ubuntu.com/community/Firewall](https://help.ubuntu.com/community/Firewall)```
Firewall

ufw enable : Turn on the firewall
ufw disable : Turn off the firewall
ufw default Allow :  Allow all connections by
default
ufw default deny :  Drop all connections by
default
ufw status : Current status and rules
ufw allow port : Allow traffic on port
ufw deny port : Block port
ufw deny from ip : Block ip adress

```

---

### Post by HiImTye on 2012-04-01
```
sudo apt-get install ufw
sudo ufw default deny
sudo ufw enable
```
that should get your ports mostly set up, after that allow individual or multiple ports for individual or multiple protocols
here's some more information
[https://help.ubuntu.com/community/UFW](https://help.ubuntu.com/community/UFW)

---

