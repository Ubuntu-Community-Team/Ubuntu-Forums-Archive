---
title: "Please point me in the right direction Server with Samba"
date: 2012-02-19
forum: New to Ubuntu
---

### Post by RichardCL on 2012-02-19
Dear Forum,

I've been using desktop for a while now so I've basic idea about how to use command line. Now I'm going to have a first crack at server building.

I've just put together a machine with Intel Atom and 2 1TB harddrives. I'm intending to build RAID mirroring via Ubuntu using the SATA ports on the motherboard.

There are a few basic questions that I need to get started. Once I know what I need to be doing, I can probably use the how tos but these fundamentals don't seem to be answered anywhere obvious.

Basically I just need a file server with access for windows and ubuntu machines from outside of home. It would be nice to have some kind of database support for addressbooks or even CRM though.


Server OS: [http://www.zentyal.org/](http://www.zentyal.org/) vs Ubuntu server.
How do I compare using Ubuntu and configuring with command line or webmin and using a pre-built solution like Zentyal?


SSH or VPN?
I tried SSH on my desktop and managed to login with private keys from my windows machines but the system admin at work told me to consider using VPN and Samba instead. Apparently the VPN is more secure because the server doesn't need to identify itself.


Access control from server or router
I have a Fritz router with internet access and port forwarding. Should I be using the router to allow specific ports or "exposed host" and controlling the access with the server. The router also supports open VPN.

Any pointers would be great. Thanks in advance.


Richard

---

### Post by drdos2006 on 2012-02-19
Here is a HOWTO which I found comprehensive and invaluable for me to start learning about server requirements. 
Uses Webmin to allow your browser to connect and modify your server settings.
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
sudo dpkg -i webmin_1.570_all.deb

Add extra libraries with :
sudo apt-get -f install

```
Uses a browser pointed to [https://your_server_IP:10000](https://your_server_IP:10000) to edit files, create shares, startup daemons etc..

regards

---

