---
title: "Does Hardy  has firewall?"
date: 2008-04-28
forum: New to Ubuntu
---

### Post by adnansanni on 2008-04-28
Hey guys? I have been looking around but don't see any firewall option in Hardy. Does Hardy have firewall? If it doesn't, what is the best firewall that I can use in hardy without problem?

And no need any virus guard in Linux unless using a mail server, right?

---

### Post by jmore9 on 2008-04-28
sudo apt-get install firestarter

then run firestarter and follow the prompts

---

### Post by TeoBigusGeekus on 2008-04-28
Ubuntu has a built in firewall called iptables. Firestarter is one of the guis to manipulate it - the most popular one. Unless you _really_ need it, don't install firestarter...

No antivirus needed whatsoever in Linux. Just be careful not to double click a virus if you have wine installed...

---

### Post by Michael.Godawski on 2008-04-28
and what is with ufw?
[http://www.ubuntugeek.com/ufw-uncomplicated-firewall-for-ubuntu-hardy.html](http://www.ubuntugeek.com/ufw-uncomplicated-firewall-for-ubuntu-hardy.html)

---

### Post by jmore9 on 2008-04-28
I am curious why not install firestarter ?  I have been using it for a long time it is easy to start easy to setup and it works good. I have the logs to show for that.

---

### Post by howlingmadhowie on 2008-04-28
just so you don't get confused, the linux kernel has a network level firewall, which routes network packets according to things like port number and protocol. this is somewhat different to the application level firewalls found in certain less professional operating systems :)

seeing as the linux kernel will drop any packet where there isn't something listening for it, you really don't need to do any more configuring for the sake of security. the linux kernel firewall is really interesting when it comes to routing, but that's another story.

by the way, the kernel firewall is called netfilter, the userland program to configure it is called iptables :)

---

### Post by tom56 on 2008-04-28
There is already a firewall running in the background. You only need to install Firestarter if you have installed advanced internet services such as a web server or mail server.

Essentially, if you're not sure then you don't need one.

---

### Post by TeoBigusGeekus on 2008-04-28
ufw: Another gui for iptables

Firestarter can be dangerous if you don't know what you are doing. You can open ports without you knowing it and all hell could break loose... Unless you really need to do some adjustments to iptables don't install firestarter or ufw.

---

### Post by adnansanni on 2008-04-28
So Ubuntu hardy heron has firewall which called iptables. Is it working by default? Right now I&#8217;ve seen in Hardy help section to security concern they asked to install firestarter for firewall. If it does have iptables then why it asked for firestarter? Only for GU interface?

---

### Post by adnansanni on 2008-04-28
Now I got it. (my net speed is slow so always I post lately.)

---

### Post by adnansanni on 2008-04-28
Thanks guys.

---

### Post by kansasnoob on 2008-04-28
Ubuntu has used iptables for some time, in Hardy ufw is installed by default, you can look here for some basic info on ufw:

[http://doc.ubuntu.com/ubuntu/serverguide/C/firewall.html](http://doc.ubuntu.com/ubuntu/serverguide/C/firewall.html)

As you can see, ufw by default is initially disabled.

To enable ufw just type "sudo ufw enable" in terminal.

Personally I like Firestarter so I went to synaptic, removed ufw, and installed Firestarter which shows up in Internet where you can configure it to your needs.

[http://www.fs-security.com/docs.php](http://www.fs-security.com/docs.php)

On Gutsy I managed to edit sudoers and get the firestarter gui and applet to start up every time I started up ubuntu, but it's really unnecessary and it was very fiddly, so I've not even tried yet in Hardy.

---

### Post by adnansanni on 2008-04-28
opps.... do I have enable "sudo ufw enable"?
I'm confused because few say iptables enable by defult.

---

### Post by kansasnoob on 2008-04-28
I'm glad I read what I wrote.

DO NOT remove ufw! It would also remove ubuntu-standard! That's BAD!

I do prefer Firestarter, but just disable ufw (sudo ufw disable) if you prefer Firestarter.

DO NOT remove it.

Sheesh, who spiked my beans?

---

### Post by TeoBigusGeekus on 2008-04-28
You should enable ufw only if you need to adjust the settings of iptables. If not, don't do anything.

---

### Post by barney385 on 2008-04-28
[http://www.fs-security.com/docs/tutorial.php](http://www.fs-security.com/docs/tutorial.php)

---

### Post by PlayGod on 2008-05-03
gnome-lokkit is a very super simple wizard-based firewall configurator. It asks all the right questions and is certainly helpful for those who will be using their laptops on shared wireless networks. I wouldn't want to get on a public wifi without at least a little help from iptables.

iptables is extremely helpful for those of us running mail and web servers. I use a nice routine that increases the delay in login prompt for every failed attempt. This pretty much kills any brute-force and harvest attempts on my web server.

caveat: this is definitely not for the inexperienced, but it may give you some insight into how iptables works:
[http://www.virtualmin.com/index.php?option=com_fireboard&Itemid=77&func=view&id=8460&catid=8#8460](http://www.virtualmin.com/index.php?option=com_fireboard&Itemid=77&func=view&id=8460&catid=8#8460)

---

### Post by agerbo on 2008-05-04
> **tom56 said:**
> There is already a firewall running in the background. You only need to install Firestarter if you have installed advanced internet services such as a web server or mail server.

Essentially, if you're not sure then you don't need one.
I enabled 
sudo ufw enable
and set
sudo ufw default deny

do I have to set up rules
I get the message
(be sure to update your rules accordingly)

maybe you are right thas it is'nt necessary;
will it make the internet slow for me

---

### Post by vishzilla on 2008-05-04
I have my firewall configured with ufw. Its a wonderful CLI tool to configure the firewall. There's a manual in Help explaining how to configure the firewall using ufw

---

