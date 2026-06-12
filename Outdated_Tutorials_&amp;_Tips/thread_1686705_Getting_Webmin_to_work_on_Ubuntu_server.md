---
title: "Getting Webmin to work on Ubuntu server"
date: 2011-02-12
forum: Outdated Tutorials &amp; Tips
---

### Post by metalf8801 on 2011-02-12
First add the Webmin repositories:
 
sudo nano /etc/apt/sources.list

add:
 
#webmin repositories 
deb [http://download.webmin.com/download/repository](http://download.webmin.com/download/repository) sarge contrib
deb [http://webmin.mirror.somersettechsolutions.co.uk/repository](http://webmin.mirror.somersettechsolutions.co.uk/repository) sarge contrib 

Exit and save 

add the GPG key you need:

sudo su (you are now root or close to it be careful and if anyone knows of a better way to do this please post it)
cd /root
wget [http://www.webmin.com/jcameron-key.asc](http://www.webmin.com/jcameron-key.asc)
apt-key add jcameron-key.asc 
exit 

sudo apt-get install webmin 

This last part is really simple which must be why I didn't find it documented anywhere 
Opening ports needed for Webmin to work:

sudo iptables -A INPUT -p tcp -m tcp --dport 10000 -j ACCEPT

You may also need to make changes the settings for ufw 

sudo ufw allow webmin
sudo ufw allow 10000 

use ifconfig to find your IP address 

[https://your](https://your) IP address:10000

I think that's it if this doesn't work please tell me

---

### Post by rajnikhil on 2011-03-02
Hi 

I've installed ubuntu server 10.04 as a guest OS using virtual box in ubuntu lucid desktop.

I've done everything you've mentioned here but I'm still unable to login i.e. the browser in desktop gives the following msg: 'The server at 192.168.1.4 is taking too long to respond.'.

Please help.

Thanks in advance.

---

### Post by Aposp on 2011-03-02
works like a charm!! i actually needed something similar to my web server!! thanks a lot!

---

