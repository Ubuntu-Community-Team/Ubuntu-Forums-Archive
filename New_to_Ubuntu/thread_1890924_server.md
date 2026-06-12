---
title: "server"
date: 2011-12-04
forum: New to Ubuntu
---

### Post by saintj0n on 2011-12-04
I am starting up a server using Ubuntu Server 10.04 LTS. I want to create a www server and Samba server on the same box.  Anyone recommend a good tutorial or website citation on how to learn this?  I have maintained windows servers but never a Linux server.  I am looking for an installation guide for a www server and would love some good examples. Thanks!

---

### Post by Doug S on 2011-12-04
I think the [Ubuntu server guide ]("https://help.ubuntu.com/10.04/serverguide/C/index.html")(I prefer the [PDF]("https://help.ubuntu.com/10.04/serverguide/C/serverguide.pdf")) is a very valuable resource. Typically, each section also contains references to other resources.

---

### Post by CharlesA on 2011-12-04
> **Doug S said:**
> I think the [Ubuntu server guide ]("https://help.ubuntu.com/10.04/serverguide/C/index.html")(I prefer the [PDF]("https://help.ubuntu.com/10.04/serverguide/C/serverguide.pdf")) is a very valuable resource. Typically, each section also contains references to other resources.
+1.

All you would need to do is install apache2 and php5 (or just install the LAMP stack)

---

### Post by matt3839 on 2011-12-04
I believe that you can choose to install a LAMP stack and Samba during installation.

---

### Post by CharlesA on 2011-12-04
> **matt3839 said:**
> I believe that you can choose to install a LAMP stack and Samba during installation.
Aye, that you can.

---

### Post by drdos2006 on 2011-12-04
Here is a HOWTO which I found comprehensive and invaluable. Uses Webmin to allow your browser to connect and modify your server settings.
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

regards

---

### Post by saintj0n on 2011-12-04
Excuse my ignorance, but what is installing :confused:PHP5 going to do?  Isn't that a programming language or something?

---

### Post by CharlesA on 2011-12-04
> **saintj0n said:**
> Excuse my ignorance, but what is installing :confused:PHP5 going to do?  Isn't that a programming language or something?

That's correct. You'll only need it if you intend on writing your pages in PHP. I use it so I can have a template for my header, navbar and footer. Templates = less work for me.

---

### Post by collisionystm on 2011-12-04
Zentyal

---

### Post by lisati on 2011-12-04
> **collisionystm said:**
> Zentyal

That might be a bit ambitious for a beginner. :)

---

### Post by collisionystm on 2011-12-04
> **lisati said:**
> That might be a bit ambitious for a beginner. :)

More like the perfect solution for a beginner lol. It's the easiest thing out there and it's not a complete nightmare like webmin ;)

---

### Post by CharlesA on 2011-12-04
> **collisionystm said:**
> More like the perfect solution for a beginner lol. It's the easiest thing out there and it's not a complete nightmare like webmin ;)
Agreed, but if they want to learn, there's nothing better then bashing yer head into a brick wall a few times.. ;)

---

### Post by Gone fishing on 2011-12-05
I was going to suggest clearOS or SME. Anyone used or know of a comparative review of Zentyal vs ClearOS vs SME.

I've never tried any of these but it looks probably easier than FreeBSD that I'm using - the documentation for setting up FreeBSD servers is good.

---

### Post by Lars Noodén on 2011-12-05
> **CharlesA said:**
> That's correct. You'll only need it if you intend on writing your pages in PHP. I use it so I can have a template for my header, navbar and footer. Templates = less work for me.

You can also do templates without PHP by using [Server Side Includes](http://httpd.apache.org/docs/2.3/howto/ssi.html).  It's simple and, with [IncludesNOEXEC](http://httpd.apache.org/docs/trunk/mod/core.html#options), it is very secure and no-maintenance.

---

### Post by collisionystm on 2011-12-05
> **CharlesA said:**
> Agreed, but if they want to learn, there's nothing better then bashing yer head into a brick wall a few times.. ;)


lol agreed. However I would never want the task of LDAP by command. Ugh I can only imagine the nightmares people experience

---

### Post by CharlesA on 2011-12-05
> **Lars Noodén said:**
> You can also do templates without PHP by using [Server Side Includes](http://httpd.apache.org/docs/2.3/howto/ssi.html).  It's simple and, with [IncludesNOEXEC](http://httpd.apache.org/docs/trunk/mod/core.html#options), it is very secure and no-maintenance.

Interesting. Thanks!

> **collisionystm said:**
> lol agreed. However I would never want the task of LDAP by command. Ugh I can only imagine the nightmares people experience

I hear you there. That sounds like a nightmare.

---

### Post by Gone fishing on 2011-12-05
> lol agreed. However I would never want the task of LDAP by command. Ugh I can only imagine the nightmares people experience 

That's how I did it with Ubuntu, Debian, Opnsuse and FreeBSD - found Ubuntu unstable, never quite got to the bottom of why, Debian I failed to get to work, Opensuse a little odd using Yast but it worked, FreeBSD followed the howto's and it worked.

---

### Post by saintj0n on 2011-12-05
So, in theory, I can load a ubuntu desktop and install webmin and have fairly good control over the server, right?  Or do I need to load more software to get my hands on the controls, so to speak?

---

### Post by collisionystm on 2011-12-05
> **saintj0n said:**
> So, in theory, I can load a ubuntu desktop and install webmin and have fairly good control over the server, right?  Or do I need to load more software to get my hands on the controls, so to speak?


The only problem I have with webmin is its a bit of a hack. It has caused me more problems than its worth

Thats why I suggested zentyal. It is actually designed for the platform its running on and has never caused me any issues.

---

### Post by CharlesA on 2011-12-05
Webmin is just a web frontend that you can use to manage your server. :)

I didn't have any problems when I used it last (A long, long time ago.. around the time 9.04 was released) but I just SSH in now.

---

### Post by collisionystm on 2011-12-05
> **CharlesA said:**
> Webmin is just a web frontend that you can use to manage your server. :)

I didn't have any problems when I used it last (A long, long time ago.. around the time 9.04 was released) but I just SSH in now.


It has that webmin script that runs at startup and I dont know... it just seemed like all of my servers ran better without it. It was like webmin was trying to automatically put its own settings in place.

Zentyal does the same, its ebox modules just ride on top of the system and almost act independently of ubuntu all together. It works well however, and thats why I like it!

---

### Post by CharlesA on 2011-12-05
> **collisionystm said:**
> It has that webmin script that runs at startup and I dont know... it just seemed like all of my servers ran better without it. It was like webmin was trying to automatically put its own settings in place.

Zentyal does the same, its ebox modules just ride on top of the system and almost act independently of ubuntu all together. It works well however, and thats why I like it!
Ick. That sounds a bit nasty tbh.

I do use some web interfaces - mostly for virtualbox and it seems a ton less clunky then webmin was for me.

---

### Post by saintj0n on 2011-12-05
Since my first objective is to run a www server, anyone have a suggestion on how to do this?  I assume the ISP provides a static IP and you just stick your webserver on it and hack away.  Is there a poor man's method that anyone knows about?

---

### Post by collisionystm on 2011-12-05
> **saintj0n said:**
> Since my first objective is to run a www server, anyone have a suggestion on how to do this?  I assume the ISP provides a static IP and you just stick your webserver on it and hack away.  Is there a poor man's method that anyone knows about?

Forward port 80 from your router to the server

---

### Post by CharlesA on 2011-12-05
> **collisionystm said:**
> Forward port 80 from your router to the server
Also make sure that your ISP allows you to run servers on your connection. If it's a residential ISP, they rarely do and more then likely block port 80 among others.

---

### Post by Lars Noodén on 2011-12-06
> **saintj0n said:**
> Since my first objective is to run a www server, anyone have a suggestion on how to do this?  I assume the ISP provides a static IP and you just stick your webserver on it and hack away.  Is there a poor man's method that anyone knows about?

Just install Apache2 or nginx and begin hacking.  If your ISP does not give you a static IP, then you can do almost (but not quite) as well using a dynamic DNS service.  DynDNS is one of several.  Also be sure that your ISP is not [blocking port 80](http://canyouseeme.org/).

---

### Post by kevinthecomputerguy on 2011-12-06
I have had only 100% awesome experiences with Webmin. But eventually we all fall back to old faithful (ssh)

---

### Post by collisionystm on 2011-12-07
> **kevinthecomputerguy said:**
> I have had only 100% awesome experiences with Webmin. But eventually we all fall back to old faithful (ssh)


oll faithful... ol reliable... fantastic lol

---

### Post by saintj0n on 2011-12-07
SSH? How do you run that?  I've never tried that.

---

### Post by CharlesA on 2011-12-07
> **saintj0n said:**
> SSH? How do you run that?  I've never tried that.
[https://help.ubuntu.com/10.04/serverguide/C/openssh-server.html](https://help.ubuntu.com/10.04/serverguide/C/openssh-server.html)

---

