---
title: "Becoming my own system-administrator possible?"
date: 2012-05-30
forum: New to Ubuntu
---

### Post by kramer65 on 2012-05-30
Hello,


For the past 5 years I've used Ubuntu as my main desktop system. This was partly because I totally support the concept of open source, partly because I was curious to how "*all that linux stuff*" worked, and partly because I wanted to understand more of the server which my (self written) php website ran on.

Fast forward to today, and I am totally comfortable using Ubuntu. Next to the GUI I'm also reasonably comfortable with the command line and I am currently testing some self-written Python programs. I am currently also working on opening up my own webshop together with a friend of mine and I am thinking of taking a self-managed cloud-vps server (from [www.cloudvps.com](www.cloudvps.com)). They provide support, but apparently the support is very minimal (you get what you pay for).

To test my skills as a system administrator I messed around with some virtualbox installs of Ubuntu server. I followed [this guide]("http://www.howtoforge.com/perfect-server-ubuntu-12.04-lts-apache2-bind-dovecot-ispconfig-3") which helped me setting up a full lamp-server including some additions like squirrelmail, spamassassin, and [ISPConfig]("http://www.ispconfig.org/") (an open source control panel). So far so good. Everything works as expected. I am currently testing [OpenCart]("http://www.opencart.com/") on it (which we'll be using for our webshop) and everything is going pretty fine.

My question is: would you think I will be able to administer my own server (with some minimal help from the hosting company in case of emergency)? Or would you say I'm missing things? Are there server-horrors which I haven't seen yet and which are bound to come or will an occasional '*service apache2 restart*' solve most problems? In short; do you think I am able to administer my own server or is that job simply too big to take on?

All tips are welcome!

Greets from an aspirant system administrator

---

### Post by Gone fishing on 2012-05-30
Why not?

What do you want your server to do?

From a background like yours I setup a server for a school in Africa that worked very well.

Squid, ldap, nfs, Apache, Webmin, Postfix, SquirrelMail  and Courier IMAP.

---

### Post by Paqman on 2012-05-30
> **kramer65 said:**
> would you think I will be able to administer my own server

Sounds like you already are. If you can set the software up and have it running ok you probably understand it well enough to troubleshoot problems, or know where to turn to for help. If you need help you've also got these forums, askubuntu.com, IRC, etc, etc.

Just one word of caution about switching to a live internet-facing machine: security. Expect the hordes to try and crack your box straight away. Install [Denyhosts]("apt:denyhosts") and set it to slap down attempted intrusions hard. Control what and how you open up to the outside world.

If you haven't already, work your way through all the relevant stuff in the [server guide]("https://help.ubuntu.com/12.04/serverguide/index.html").

---

### Post by kramer65 on 2012-05-30
> **Paqman said:**
> Sounds like you already are.
:o

> **Paqman said:**
> If you can set the software up and have it running ok you probably understand it well enough to troubleshoot problems, or know where to turn to for help. If you need help you've also got these forums, askubuntu.com, IRC, etc, etc.

I am indeed comfortable using apt-get and editing files using vi. I wouldn't say I *always* know what I am doing, but I do feel comfortable messing around. These forums have indeed been the greatest community I've come around on the internet. I should actually thank you guys for having learned all that I have.
One question about the IRC-channels (I've never been on IRC in my life), where can I actually find them? It would be great to talk to people if our server is live and I get into total stress because some service crashes..

> **Paqman said:**
> Just one word of caution about switching to a live internet-facing machine: security. Expect the hordes to try and crack your box straight away. Install [Denyhosts]("apt:denyhosts") and set it to slap down attempted intrusions hard. Control what and how you open up to the outside world.
Security is indeed what always scares me about the internet. My last website (which I sold) once got under a heavy ddos attack which crashed the whole (dedicated) server. I didn't notice until I saw the site was down and once I notified my hosting they hadn't seen it yet either. A restart solved the problem apparently. Afterwards I was actually thinking; if they hadn't even noticed yet, and all it took was a restart, then I would have been able to solve it myself.
Seeing that attack was back in 2005 and I think things like denyhosts didn't exist yet I guess I will have less trouble with it now. On my testserver I actually installed fail2ban. Would you recommend denyhosts or fail2ban?

> **Paqman said:**
> If you haven't already, work your way through all the relevant stuff in the [server guide]("https://help.ubuntu.com/12.04/serverguide/index.html").
Thanks for the tip! That is a great way to start indeed!

---

### Post by Paqman on 2012-05-30
> **kramer65 said:**
> 
My last website (which I sold) once got under a heavy ddos attack which crashed the whole (dedicated) server.


Not a lot you can do about that, unfortunately.

> 
I didn't notice until I saw the site was down and once I notified my hosting they hadn't seen it yet either. A restart solved the problem apparently. Afterwards I was actually thinking; if they hadn't even noticed yet, and all it took was a restart, then I would have been able to solve it myself.


I use [Uptime Robot]("http://www.uptimerobot.com/"), but other equivalents exist. It checks every 5 mins and will send you an email if your site goes down.

> 
Seeing that attack was back in 2005 and I think things like denyhosts didn't exist yet I guess I will have less trouble with it now. On my testserver I actually installed fail2ban. Would you recommend denyhosts or fail2ban?


I've not used fail2ban, denyhosts seems like it had much easier config to me. Neither will actually protect you from DDOS coming over HTTP ports, but if nothing else they'll keep all the script kiddies hammering SSH/FTP from spamming your logs.

---

### Post by kramer65 on 2012-05-31
@Paqman

Thanks again for those answers. I didn know uptime robot and I'll definitely use it once our new webshop is up and running.

One more question. Once my webserver is up an running with security updates set to automagically, the only things I need to do are the following right?:
[LIST]
[*]restart in case of a crash and find the cause (how do you actually do that?)
[*]install new software if I need it (just a simple apt-get)
[*]update to Ubuntu 16.04 LTS in 2017 (or earlier if I need the new features)
[/LIST]

Is there anything I am missing here? Being a system administrator for one server suddenly seems to be so easy.. :-\"

---

### Post by Paqman on 2012-05-31
> **kramer65 said:**
> Once my webserver is up an running with security updates set to automagically, the only things I need to do are the following right?:
[list]
[*]restart in case of a crash and find the cause (how do you actually do that?)
[/list]


Your logs would be a good place to start. It really depends what caused the crash, which depends on what you've got installed. The machine is only as stable as the applications it runs.

> 
[list]
[*]install new software if I need it (just a simple apt-get)
[*]update to Ubuntu 16.04 LTS in 2017 (or earlier if I need the new features)
[/LIST]


I would wait for 16.04.1 (or 14.04.1) myself. Waiting for the point release gives it time to shake out any residual bugs. Release-day images are often still a little flaky.

Incidentally, Precise will get new kernels backported from now on which reduces some of the need to do a full upgrade.

As for other maintenance tasks, don't forget backups and taking a look at the logs regularly.

---

