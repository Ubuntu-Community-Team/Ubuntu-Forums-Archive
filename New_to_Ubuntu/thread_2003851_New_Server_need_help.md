---
title: "New Server need help"
date: 2012-06-14
forum: New to Ubuntu
---

### Post by mike551345 on 2012-06-14
So i have just set up a Ubuntu Server 12.04. The server is running on a Dell Dimension 2400 (i think its from like 2001ish). The computer has a intel Pentium 4 processor, 1.5 gb ram, and 80gb hdd (going to make it bigger soon but need some money). I want to make it so the server is a file sharing server between me and my friends. so i want it to be able to let my friends create there own account or if its easier for me to make there account what ever works. 

also the server is running no GUI so it command line based. i will take videos or wrriten tutorials. this is my second go around with trying to find help set it up. last time i installed a bunch of stuff and didnt know how to get rid of it. so hope you guys can help.

---

### Post by drdos2006 on 2012-06-14
Here is a HOWTO which I found comprehensive and invaluable for me to start learning about server requirements. 
Uses Webmin to allow your browser to connect and modify your server settings on your network.


> 
Are you using the most current version of this how-to?
Version numbers are located @ top right of this page. Latest versions are available at my homepage [http://woodel.com](http://woodel.com)
Under the Solutions tab
"Setting up a Linux Server, Start to Finish, using Webmin". By Kevin Elwood



And on your server..........

```

Logon to your server and download from your server with :
sudo wget http://prdownloads.sourceforge.net/webadmin/webmin_1.580_all.deb

Install with :
sudo dpkg -i webmin_1.580_all.deb

Add extra libraries with :
sudo apt-get -f install

```
Uses a browser pointed to [https://your_server_IP:10000](https://your_server_IP:10000) to edit files, create shares, startup daemons etc..

regards

---

