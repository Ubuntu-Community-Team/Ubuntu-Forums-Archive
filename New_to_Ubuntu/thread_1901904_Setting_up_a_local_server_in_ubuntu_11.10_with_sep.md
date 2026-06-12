---
title: "Setting up a local server in ubuntu 11.10 with separate packages"
date: 2011-12-29
forum: New to Ubuntu
---

### Post by kevincmaker on 2011-12-29
im using ubuntu 11.10

i have downloaded the following components separately....

1. filezilla (FTP client)

2. MySQL server

3. PHPMYADMIN along with apache server

I just want two things to know...

1. are the above things enough for setting a local server?

2. how to configure the client and servver??

Any valid answers would be greatly helpful !!! :)

Thanks!

---

### Post by drdos2006 on 2011-12-29
You are going to have to do some heavy reading to set up your first server.
Zentyal will get your machine running in an office type environment while you learn the more detailed operations of a server. [http://www.zentyal.com/](http://www.zentyal.com/)

Here is a HOWTO which I found comprehensive and invaluable for me to start learning about server requirements. Uses Webmin to allow your browser to connect and modify your server settings.
You could also install the Desktop plus install and run the server as a virtual machine using Virtualbox and that is how I run my testing websever.

> 
Are you using the most current version of this how-to?
Version numbers are located @ top right of this page. Latest versions are available at my homepage [http://woodel.com](http://woodel.com)
Under the Solutions tab
"Setting up a Linux Server, Start to Finish, using Webmin". By Kevin Elwood



And on your server..........

```

Logon to your server and download from your server with :
sudo wget http://prdownloads.sourceforge.net/webadmin/webmin_1.570_all.deb

Install with :
sudo dpkg -i webmin_1.550_all.deb

Add extra libraries with :
sudo apt-get -f install

```

regards

---

