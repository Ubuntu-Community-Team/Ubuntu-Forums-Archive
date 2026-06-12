---
title: "Best way to start a new simple server?"
date: 2018-07-07
forum: New to Ubuntu
---

### Post by l0l59 on 2018-07-07
Hello,

I recently got into Linux based OS. I downloaded Xubuntu and have been enjoying it so far. I wanted to create a server, but I wanted to know how to create one and I need to know what is the most simplest Ubuntu Os (flavour) because my computer is very under powered, running at 5gb of memory only. I am running Xubuntu on a virtual system, and I also want to run these servers on the virtual system. Any suggestions on how to do it?

Thanks,
L0L59

---

### Post by yancek on 2018-07-07
Ubuntu has a server version as well as a Desktop version.  The server version is much smaller and does NOT have a GUI.  I don't see a server version on the Xubuntu page.  What kind of server, web server, mail server?  The link below explains installing a web server (LAMP server) on Ubuntu 18.04, should be the same method on Xubuntu.

[https://www.digitalocean.com/community/tutorials/how-to-install-linux-apache-mysql-php-lamp-stack-ubuntu-18-04](https://www.digitalocean.com/community/tutorials/how-to-install-linux-apache-mysql-php-lamp-stack-ubuntu-18-04)

Simpler method explained at the link below.

[https://www.linode.com/docs/web-servers/lamp/install-lamp-stack-on-ubuntu-18-04/](https://www.linode.com/docs/web-servers/lamp/install-lamp-stack-on-ubuntu-18-04/)

If that's not what you want you will need to post more details.

---

### Post by l0l59 on 2018-07-07
> **yancek said:**
> Ubuntu has a server version as well as a Desktop version.  The server version is much smaller and does NOT have a GUI.  I don't see a server version on the Xubuntu page.  What kind of server, web server, mail server?  The link below explains installing a web server (LAMP server) on Ubuntu 18.04, should be the same method on Xubuntu.

[https://www.digitalocean.com/community/tutorials/how-to-install-linux-apache-mysql-php-lamp-stack-ubuntu-18-04](https://www.digitalocean.com/community/tutorials/how-to-install-linux-apache-mysql-php-lamp-stack-ubuntu-18-04)

Simpler method explained at the link below.

[https://www.linode.com/docs/web-servers/lamp/install-lamp-stack-on-ubuntu-18-04/](https://www.linode.com/docs/web-servers/lamp/install-lamp-stack-on-ubuntu-18-04/)

If that's not what you want you will need to post more details.

Hello

Thank you very much. I will try out and read the links while Ubuntu Server downloads. :)

Thanks again,
L0L59

---

### Post by SeijiSensei on 2018-07-07
[http://cdimage.ubuntu.com/ubuntu-server/bionic/daily/current/](http://cdimage.ubuntu.com/ubuntu-server/bionic/daily/current/)

Start simple. Try setting up Samba to share files with Windows machines, and NFS for sharing with *nix clients. Next you might try a web server. I recommend installing the lamp-server meta package with
```
sudo apt install lamp-server^
```
and then maybe [Wordpress]("http://wordpress.org/").

---

### Post by rickdiaz on 2018-07-10
[FONT=&quot]The reason is simple: Ubuntu Server is easy to administer, well documented, and has a pretty low learning curve, especially if you&#8217;ve ever used desktop Ubuntu.[/FONT]

---

### Post by Tadaen_Sylvermane on 2018-07-10
First thing about setting up a server. What do you need it for? What are you trying to serve? 

Once you answer those questions you can move forward. Those 2 questions determine everything else.

---

### Post by Habitual on 2018-07-12
The SimpleHTTPServer module that comes with Python is a simple HTTP server that provides standard GET and HEAD request handlers. Why should I use it?...
[How to use SimpleHTTPServer]("http://www.pythonforbeginners.com/modules-in-python/how-to-use-simplehttpserver")

---

