---
title: "how to secure apache webserver"
date: 2012-01-07
forum: New to Ubuntu
---

### Post by norcal on 2012-01-07
Hello, 

I am setting up home web server. mostly to post pics for family. 

After installing apache web server,  I created a new group and added one user who is on my other machine and will be uploading files . I gave this user permissions to the www folder only. Is this the best way to keep things secure?

Also would you recommend using webmin? if not are there alternatives.

I tried to use the perfect server tutorial but too complicated for me. 

thanks

---

### Post by drdos2006 on 2012-01-07
Here is a HOWTO which I found comprehensive and invaluable for me to start learning about server requirements. Uses Webmin to allow your browser to connect and modify your server settings.
You could also install the Desktop plus install and run the server as a virtual machine using Virtualbox and that is how I run my testing websever.
Use this HOWTO and look for “Protected Web Directories”.
I recommend Webmin for easy server control.

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

