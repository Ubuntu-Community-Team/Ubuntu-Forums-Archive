---
title: "help with http server"
date: 2013-09-16
forum: New to Ubuntu
---

### Post by coyoty on 2013-09-16
Hi, I am working on a website project for my uncle, and I would like to show him my progress. I have set up the server and I am using it but my problem is that I am on a campus internet and I cannot forward port 80. Uploading my work to a free webhost is not very secure I guess. So does anyone know how can someone connect to my webserver from their browser without portforwarding or uploading to another webhost? Thanks

---

### Post by Lars Noodén on 2013-09-16
If your uncle has a publicly accessible machine running ssh you could do a reverse tunnel.  That would connect one port on his machine to one port on your machine. 

If your uncle does not have a publicly accessible machine, then either free or paid-for hosting is probably your best option.  You can use [htaccess](http://httpd.apache.org/docs/2.2/howto/htaccess.html) to put a weak password on it.

---

### Post by coyoty on 2013-09-16
can you please help me with the reverse tunnel? he has a mac laptop

---

### Post by Lars Noodén on 2013-09-16
1. Great. OS X has openssh-server built in. It can be turned on in System Preferences:

    AppleMenu-> System Preferences-> Sharing-> Remote Login

He'll have to set up an account for you to log in with.

2. He'll have to set up his modem to forward port 22 to his Mac. The details of that vary from brand to brand and model to model. But there should be a menu somewhere that allows it.  But that will allow you to log into his machine using ssh.  

3. Once you can log into his machine from wherever you are at, you can set up a reverse tunnel from your machine to his machine.  From your machine, connect to his machine:

```

ssh -R 8888:localhost:80 coyoty@xx.yy.zz.aa

```

Substitute the ip number of his machine above.  Above, port 80 on your machine is being forwarded to port 8888 on his machine.  The reverse tunnel will then stay open as long as you keep that ssh session open.  For background, read the manual page for ssh about the option -R.  It can be handy to read about -f -N and -T too.

4.  Once you have the reverse tunnel, he can connect to [http://localhost:8888/](http://localhost:8888/) to see your site (which is really on port 80 on your machine)

5.  When you are done, you can close the ssh session and then have him turn off Remote Login.

That's a lot of steps, but once you've done it the first time, it is easy.

---

### Post by coyoty on 2013-09-16
Thank you very much !

---

