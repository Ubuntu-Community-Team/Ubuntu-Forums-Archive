---
title: "Setting up Ubuntu Server on Raspberry Pi (latest from Amazon - Jan, 2018)"
date: 2018-01-28
forum: New to Ubuntu
---

### Post by oliver172 on 2018-01-28
I am ready to ditch Apple's MacOS Server since Apple is basically ditching it anyway in 2018 per their public deprecation statements.

However, I'm nervous about the direct jump to a product like Ubuntu Linux server since my experience with Mac is that there are nice at least semi-GUI tools to help you. My experience with Linux is that you are thrown in to command-line, often compile-it-yourself, Hell right away with often little middle ground. AKA: the deep end of the pool.

However, my needs really aren't *that* difficult so I'm assuming it wouldn't actually be that difficult for[B] Ubuntu Server on Raspberry Pi 3, to:
[/B]
1. Install Java 8 or 9.

2. Install Tomcat Server 8.5 with SSL (SSL already configured on Mac OS Server with a Java Keystore so that part should directly translate).

3. (Maybe if not toooooo difficult, always had problems in the past, try to get Apache and Tomcat to work together for incoming Requests that should go to Tomcat).

4. Set up DDNS. (Sorry Comcrap, I don't want your ridiculously-expensive, business service!)

5. Set up a basic firewall. Port forwarding already working on Apple Airport Extreme thanks to nice integration (auto setup) with Mac OS Server.

6. Set up my hostname (company.com) for access.

------

Setting up DDNS on the mac was easy, for example, since there were available tools for it. (Maybe so too, for Linux.).

My goal is just to be able to have users be able to access web services using various ports.

If I can actually also get Apache to pass requests to Tomcat (for, say, Servlets) that would be a bonus (again, this is easy using Easy Apache on Linux Hosting, but **cPanel does not support Java 8**, leaving me out in the cold there, too).

----

I would really appreciate any comments about Raspberry Pi's applicability to what I am trying to do and my above list of technical goals' achievability.

Thanks much! :)

---

### Post by managerceo1 on 2018-01-28
[https://medium.com/a-swift-misadventure/how-to-setup-your-raspberry-pi-2-3-with-ubuntu-16-04-without-cables-headlessly-9e3eaad32c01](https://medium.com/a-swift-misadventure/how-to-setup-your-raspberry-pi-2-3-with-ubuntu-16-04-without-cables-headlessly-9e3eaad32c01)

Regards!

---

### Post by HermanAB on 2018-01-28
But, but, but... Raspbian: 
[https://www.raspbian.org/](https://www.raspbian.org/)

---

### Post by oliver172 on 2018-01-28
OK, good to know....but is is "straightforward" to do all the setup things I need to do with RP and Raspbian per my original posting or am I better off creating a VM or even buying a cheap desktop computer?

Thanks,

---

### Post by tps-mail on 2018-01-29
It's pretty straightforward. If you install the full image (not the minimal version), you have all the GUI tools to help you, along with the command line, and you don't have to have the GUI running the whole time eating resources, just when you want to do something. All the tools are available.

---

### Post by HermanAB on 2018-01-30
I wrote this a few weeks ago:
[http://www.aeronetworks.ca/2017/12/raspberrypi-3-headless-with-ssh.html](http://www.aeronetworks.ca/2017/12/raspberrypi-3-headless-with-ssh.html)

---

### Post by mastablasta on 2018-01-30
linux server is configured using text files which can also be changed via command line. 

there a couple of good GUi available for linux server administration:
Ajenti (available on various Linux distros)
Openmediavault (comes as Debian based distro)
Nethserver (comes as CentOS based distro)
Zentyal (SBS replacement, Ubuntu based)
ClearOS (CentOS based)

Then you have a couple of BSD based ones such as NAS4free, FreeNAS... As i understand BSD is closer to DarwinOS and Unix which are used as base for Mac.

Anyway for more professional use and if you plan to load the server a lot i wouldn't recomend using the RaspberryPi. you can get a reliable micro server instead.

Also the points you mention are about applications (services) not the OS itself.

---

### Post by tps-mail on 2018-01-30
Herman, 
  Nice write up. However, getting ssh enabled is even easier, espscially for people that are not currently running Linux.  [http://unslept.com/~tps/blog/index.php?/archives/16-Raspberry-Pi-Pixel-Image.html](http://unslept.com/~tps/blog/index.php?/archives/16-Raspberry-Pi-Pixel-Image.html)

---

