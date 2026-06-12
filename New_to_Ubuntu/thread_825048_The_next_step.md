---
title: "The next step?"
date: 2008-06-10
forum: New to Ubuntu
---

### Post by FlyinRedneck on 2008-06-10
After running Ubuntu and experimenting with some other distributions, i have decided to reach a goal during this summer. I have no background on servers (I am just 16). This summer I would like to put together a small server just to learn how. Does anyone know good resources for an absolute beginner to servers. I need a basic knowhow of how the different type of servers work and how to put together a machine to run all the necessary programs to create an Email server, File/FTP server, web server, and even a game server. Please help me fulfill my goal this summer of obtaining this goal. 

Or should you suggest that i take some other necessary steps first? Please tell me...

---

### Post by barney385 on 2008-06-10
Another relevant thread: [http://ubuntuforums.org/showthread.php?t=803123](http://ubuntuforums.org/showthread.php?t=803123)

[http://www.howtoforge.com/openldap-s...ler-ubuntu7.10]("http://www.howtoforge.com/openldap-samba-domain-controller-ubuntu7.10")


[https://help.ubuntu.com/community/Servers](https://help.ubuntu.com/community/Servers)

---

### Post by FlyinRedneck on 2008-06-10
That isn't quite the same... i am not an IT professional, I need the basics first. I am new to servers, i know what they are and i have a vague knowledge of what they do, but that is the limit of my knowledge. I learn things best when i interact with them. I have an extra computer to experiment with this. I am not actually trying to create a working server for a company. I am trying to learn how servers work and how to use Ubuntu Server efficiently. This is merely a quest for knowledge.

---

### Post by Darkade on 2008-06-10
Hey that's just what I did last summer :lolflag: I'm 19 by the way

Ok first of all you should learn a few things about HTML and CSS
[http://www.htmlcodetutorial.com/](http://www.htmlcodetutorial.com/) is a great site to learn a bit of both

Next you should learn of PHP and probably MySQL
First of all instal apache, mysql, php modules for apache, and mysql for php modules. All of them are in the repositories so if you make a quick search in Synaptic you shouldn't have a problem (sorry for not givin more instructions on install, I'm not in my PC rightnow, but I promaise I'll give you more help if you wish)

[http://php.net](http://php.net) Is the php site and it has tons of tutorials
[http://www.phpmyadmin.net/home_page/index.php](http://www.phpmyadmin.net/home_page/index.php) You probably will want to install this since it's a great tool for managing your MySQL databases

now If you want to go for the full thing and installing a Mail server read this howto, it's really great, explicit and designed for ubuntu so you shouldn't have to many problems
[http://flurdy.com/docs/postfix/](http://flurdy.com/docs/postfix/)

I really don't know hot to setup a DNS so you may want to check [http://www.dyndns.com/](http://www.dyndns.com/) they offer a free service in wich your DNS updates instantly if your IP address changes I use their service and it's quite good

Finally I strongly recomend you to have a rather good internet connection for upload, I think avobe 1MB of speed for upload will be enough for a small site. I have just 256Kb of upload :( and my text site is a bit of sloooooow for loading some text and not to talk about Images or music (but I'm planning to upgrade my connection :D:D:D) if you want to chek it you can visit [http://arcadelair.homelinux.net](http://arcadelair.homelinux.net) but it's in spanish LOL

Hope it works for you and If you want any help I'll be glad to help you

---

### Post by kebes on 2008-06-10
My recommendation would be to start with getting a web-server running. It's pretty easy... but you will learn a lot, and this will make setting up other servers easier. (Getting a mail server running is usually more troublesome, for instance.)

A good place to start is search for basic guides for getting a "LAMP stack" running on Ubuntu. LAMP stands for "Linux Apache MySQL PHP" (Linux is the operating system; Apache is the web-server typically used on Linux; MySQL is a database system; PHP is a scripting language commonly used for web-pages).

[This guide]("https://help.ubuntu.com/community/ApacheMySQLPHP") provides a basic intro for installing. [This guide ]("http://www.ubuntugeek.com/ubuntu-704-feisty-fawn-lamp-server-setup.html")provides some screenshots, including installing the initial OS. (By the way, you don't need to install the server version of Ubuntu to run a server; you can install the normal desktop version and then install the server components into that... this is usually easier for beginners because at least you have a GUI and desktop environment to work in while you are learning.)

Honestly the best way is to just dive right in and try it (since you have a spare computer). When you run into problems (and you will!), just ask on the forums and I'm sure you'll get lots of help.


Edit: [This guide]("http://ubuntuforums.org/showthread.php?t=223805") looks good, too.

---

### Post by FlyinRedneck on 2008-06-10
Thank you very much Darkade, since i know HTML and CSS pretty well i think i will start with Mysql and PHP... That is a fantastic site by the way... But there is still a few more things, I still need information on creating a Gaming server in Ubuntu server... 

Any more information not mentioned, or if anyone knows more great resource sites is welcome to post...

---

### Post by gr4nf on 2008-06-10
Here's my recommmendation:

open a terminal, and run the command:
```
sudo apt-get install apache2
```
to get the application "apache2", which is a good web server.

in the directory /var/www, there is a file called "index.html", or at least there will be when you install apache2. That is the default homepage of your computer (which just became a server, now that you have apache2!). To look at this hompage, run the command:
```
ifconfig
```
and look for your ip address. If you are behind a router, it will probably be 192.168.?.???. If not, it may be any four number combination, seperated by periods.

Now, get on a local computer, and go to the web browser. In the URL bar, type [http://(IP](http://(IP) ADDRESS HERE) and you will see your index.html file. You may edit this file on your sever with any text editor.

Good Luck!

---

### Post by Darkade on 2008-06-10
What do you mean by a gaming server?

(:lolflag: I'm also planing of setting up a Ragnarok-like server with some friends of mine LOL)

---

### Post by FlyinRedneck on 2008-06-10
I would like to know how to run and manage the dedicated server files that are free for just about any game out there e.g. Battlefield 2, Halo, basically any game with linux dedicated server files.

---

### Post by gr4nf on 2008-06-10
> What do you mean by a gaming server?

Like a dedicated server? For a game like "Tremulous"? For that, you might need a static IP, or at least server web access. That's somewhat expensive (maybe $100 /year). It is also quite difficult to get a home server to connect directly to the net. You would need to bypass your router (if you have one), and it would be wise to set up a firewall in between the "big bad net" and your home desktop (also a very fun project). Look into IP Cop, a Linux distro designed to make old, useless computers act as firewalls.

---

### Post by Paqman on 2008-06-10
I'd hold off on actually installing Apache for now. At least until you've read up a bit about security.

Either that or do it on a box that isn't facing the internet.

---

### Post by gr4nf on 2008-06-10
To determine how to better assist you, and not expose you to destructive things like viruses and unprotected computers, it would be invaluable to know as to whether  you had a firewalled router.

---

### Post by FlyinRedneck on 2008-06-10
With the dedicated server thing, $100 a year is nothing for me... I also know my router through and through, and yes, it is firewalled ... However the security may be a problem... are there any good resources on that?

---

### Post by kebes on 2008-06-10
> **gr4nf said:**
> you might need a static IP, or at least server web access. That's somewhat expensive (maybe $100 /year).
By the way, you can get around the dynamic IP issue by signing up for a free domain redirect service. For instance, [no-ip]("http://www.no-ip.com/") will provide you with a redirect, and give out a small Linux utility that will update the redirect if/when your IP address changes.

> It is also quite difficult to get a home server to connect directly to the net. You would need to bypass your router (if you have one)
I have not found it to be too difficult. You're right that you will need to open ports on the router. Also, most ISPs block port 80 (the standard port for web traffic), but you can switch to an alternate port.

(Note also that your terms of service for your Internet access may actually stipulate that you can't run certain kinds of servers.)

> it would be wise to set up a firewall in between the "big bad net" and your home desktop (also a very fun project).
Good point. If you have a hardware firewall (e.g. a router), and you configure the Linux firewall properly (e.g. install Firestarter to make this easier), then you should be safe.

---

### Post by gr4nf on 2008-06-10
the following is a rather helpful one:
[http://www.htmlgoodies.com/beyond/security/article.php/3604136](http://www.htmlgoodies.com/beyond/security/article.php/3604136)

---

### Post by Darkade on 2008-06-10
> **gr4nf said:**
> You would need to bypass your router (if you have one), and it would be wise to set up a firewall in between the "big bad net" and your home desktop (also a very fun project). Look into IP Cop, a Linux distro designed to make old, useless computers act as firewalls.

Bypass a router ain't that hard most homerouters have simple interfaces you can use to setup that things check [here]("http://portforward.com/routers.htm") to find out if there's a tutorial to "port forward"** to your computer. As far of the firewall I think that if you plan just to have a small server,for kind of a personal site, you don't need it that much, just a safe linux configuration and a simple firewall would be fine. BUT if you are going with the dedicated server, wich I really have no idea how to set up, you really should have a firewall. I've seen IP cop working and it's simple and usefull. The down side is that you'd need another pc, but and old one would be enough.

**port forwarding is the act of letting you router know that whenever someone looks for a port related to your IP address redirect that request to an specific computer or device

---

### Post by Darkade on 2008-06-10
> **kebes said:**
> 
I have not found it to be too difficult. You're right that you will need to open ports on the router. Also, most ISPs block port 80 (the standard port for web traffic), but you can switch to an alternate port.

(Note also that your terms of service for your Internet access may actually stipulate that you can't run certain kinds of servers.)



Yeah that's a fact you should first know if you ISP allows you to set up a server or if port 80 ain't blocked. But using another port is not that hard

---

