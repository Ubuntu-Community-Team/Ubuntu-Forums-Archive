---
title: "Home web"
date: 2012-11-07
forum: New to Ubuntu
---

### Post by nicksimpson32 on 2012-11-07
Problem 1 

Hi guys, i have a fresh install ( other than xrdp ) of ubuntu 12 04 lts desktop. The server is connected to the internet and i can internally remote connect to server, however ubuntu/firefox and updates etc do not work ie no internet access. 

Problem 2

I have tried for 4 weeks, with different LAMP/XAMP packages and numerous forum asks and different web advice pages, to try and set up the following - without success might i add, hence the fresh install.
Please, please, please, please, please, please, please, please, please, can anyone point me towards a workable solution -
My ask
3 x websites on home server, mysite.net, mysite.org, mysite.com,
Web sites are connected to my ip via Dyndns,
I would like the sites to be able to be accessed with above names only (not followed with ports or file paths etc)
I am with Talktalk so I hope they were honest when I enquired about blocked ports, they basically said they dont block ports.
I am able to sort firewalls and port forwarding, when the sites are sorted.

Thank you in advance.

---

### Post by 2F4U on 2012-11-07
> Problem 1 

Hi guys, i have a fresh install ( other than xrdp ) of ubuntu 12 04 lts  desktop. The server is connected to the internet and i can internally  remote connect to server, however ubuntu/firefox and updates etc do not  work ie no internet access. 

- Does it have a static or variable IP address?
- Where does it get DNS servers from? On static IP, you need to configure them manually, on dynamic, the SHOULD come from your DHCP server.
- Can you ping e. g. [www.google.com?](www.google.com?)
- What is your setup (router, dial-in, etc.)?

---

### Post by Lars Noodén on 2012-11-07
You can install the whole LAMP stack by using Synaptic or apt-get:

```

sudo apt-get update
sudo apt-get install lamp-server^

```

However, if you don't neend the whole thing, you can install just the parts you need. 

```

sudo apt-get install apache2

```

By default you will get one virtual host, but you can add more.  The configuraiton file will be /etc/apache2/sites-available/default and the data will be held in /var/www.  Of course you can change that around or add another virtual host.

---

### Post by pkadeel on 2012-11-07
> **nicksimpson32 said:**
> Problem 1 
3 x websites on home server, mysite.net, mysite.org, mysite.com,
Web sites are connected to my ip via Dyndns,
I would like the sites to be able to be accessed with above names only (not followed with ports or file paths etc)
I am with Talktalk so I hope they were honest when I enquired about blocked ports, they basically said they dont block ports.
I am able to sort firewalls and port forwarding, when the sites are sorted.
Thank you in advance.

If your sites do not need PHP or MySQL then all you need is apache2 and configuration of virtual hosts for your 3 sites. I found [this guide]("https://help.ubuntu.com/12.04/serverguide/httpd.html") very helpful and easy to follow.

Just remember while configuring your apache that you need it to listen on your ip address and port 80

---

### Post by sandyd on 2012-11-07
> **nicksimpson32 said:**
> Problem 1 

Hi guys, i have a fresh install ( other than xrdp ) of ubuntu 12 04 lts desktop. The server is connected to the internet and i can internally remote connect to server, however ubuntu/firefox and updates etc do not work ie no internet access. 

Problem 2

I have tried for 4 weeks, with different LAMP/XAMP packages and numerous forum asks and different web advice pages, to try and set up the following - without success might i add, hence the fresh install.
Please, please, please, please, please, please, please, please, please, can anyone point me towards a workable solution -
My ask
3 x websites on home server, mysite.net, mysite.org, mysite.com,
Web sites are connected to my ip via Dyndns,
I would like the sites to be able to be accessed with above names only (not followed with ports or file paths etc)
I am with Talktalk so I hope they were honest when I enquired about blocked ports, they basically said they dont block ports.
I am able to sort firewalls and port forwarding, when the sites are sorted.

Thank you in advance.

Few Questions
- Is the server directly connected to the internetn (i.e. connected to cable modem, DSL, .etc .etc), or through a router?
- If you don't need php/mysql, just run
```

sudo apt-get install apache2
``` to install apache2. You can then configure the virtual hosts inside /etc/apache2/sites-avaliable. An example called 'default' has already been provided there.
 Else, run
```

tasksel
```
and use the spacebar to add a star beside 'web server'

---

### Post by nicksimpson32 on 2012-11-07
To all who have replied, thank you for your time, i will mark this thread as solved and open a new hread as and if i need to during the installs.

---

