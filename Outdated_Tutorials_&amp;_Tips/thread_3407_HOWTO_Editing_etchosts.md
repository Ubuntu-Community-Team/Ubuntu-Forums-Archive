---
title: "HOWTO: Editing /etc/hosts"
date: 2004-11-05
forum: Outdated Tutorials &amp; Tips
---

### Post by FLeiXiuS on 2004-11-05
Here is a quick how to, to edit your /etc/hosts file.
The $ represents a line of code you may enter in a terminal.

Open /etc/hosts with your favorite text editor.  Remember to use sudo.

```

**Format:**
<IP> <HOSTNAME>.<DOMAIN> <ALIAS>

**Example:**
127.0.0.1 localhost.localdomain localhost

```

_IP_
Replace the <IP> with the IP of your system. If your running DHCP do not worry about editing this file.  To detect your IP address run ```
$ lsconfig
``` Then browse for the connected interface (eth0, wlan0, etc)

_Hostname_
Replace the <HOSTNAME> to your systems hostname.
```

**To view current hostname:**
$ hostname

**To change hostname:**
$ sudo hostname 'enterhostname'
(without quotes)

```

_Domain Name_
The domain name can be anything you like unless it must be resolv, which then you must use /etc/resolv.conf.  But thats another issue i'll cover later! :o 

_Alias_
Alias are simply another way to combine a set of arguments.  When you create a hosts file, its simply creating a list of hosts on the network, or locally.  Its much easier to understand if you kept the alias the same as the hostname.  It saves a lot of trouble with debugging and troubleshooting.  But you are free to use whatever you like.


That should help you out.  Please comment!

---

### Post by diebels on 2004-11-06
Nice. You can make shortcuts for webpages with alias
```
216.239.37.99 www.google.com g
```Type ctrl+L,g,enter in firefox to go to google.

---

### Post by hayalci on 2004-12-01
you can do the same more practically by giving a keyword to a bookmark, in firefox.
Just go to bookmars->manage bookmarks
and open the bookmark's properties, entering the keyword and
clicking OK.

this link describes more, quick searches, which in my opinion are great:
[http://www.mozilla.org/products/firefox/smart-keywords.html](http://www.mozilla.org/products/firefox/smart-keywords.html)

---

### Post by victorbrca on 2007-02-22
Would anyone know why this would not work on Edgy?
  
  I'm trying to access my webserver in my LAN, however due to my firewall I cannot use the external address, I have to use my internal address to my DMZ. 

  I'd like to have my translation done like this HOST.DOMAIN = DMZ IP. It's very useful when looking at information posted on the web with the source on ur webserver.

```
victor@victor-laptop:~$ cat /etc/hosts
127.0.0.1       localhost
127.0.1.1       victor-laptop
10.10.0.2     www.mysite.dyndns.org    home
72.14.203.99    www.google.ca   g

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

``` 

  The alias for google is also not working.

  I also restarted my network and logged out and back in, but no doughnut..

```
sudo /etc/init.d/networking restart
```


Thanks,


Vic.

---

### Post by meonkeys on 2009-07-07
Related links:
[LIST]
[*][Why does 127.0.1.1 appear in /etc/hosts?]("http://www.linuxquestions.org/questions/linux-networking-3/what-does-127.0.1.1-mean-623421/#post3067894")
[*][Should /etc/hostname contain the whole FQDN?]("http://lists.debian.org/debian-user/2007/09/msg00003.html")
[*][More examples working with hostnames]("http://www.linuxquestions.org/questions/slackware-14/hostname-fqdn-etchosts-setup-302189/")
[/LIST]

What I can't find is a simple, complete best/standard practices guide on how to set the hostname for a laptop and for a box with a static IP and FQDN.

---

### Post by mcdragon on 2010-06-15
Should I add my static IP address in the hosts file as well as the one I use on my local network?

Example:
```
127.0.0.1	localhost
127.0.1.1	mmpcubuntu
192.168.0.5	mmpcubuntu

```

---

### Post by cejohnsonsr on 2010-09-17
The reason this line won't work:

[B][COLOR=Red]10.10.0.2     [www.mysite.dyndns.org]("http://www.mysite.dyndns.org")    home

[/COLOR][/B][COLOR=Red][COLOR=Black]is because 10.10.0.2 is a private ip address & [www.mysite.dyndns.org]("http://www.mysite.dyndns.org") has to resolve to a public ip address. To use [www.mysite.dyndns.org]("http://www.mysite.dyndns.org") as the FQDN you need to enter the router's public ip address & set the router to forward port 80 traffic to your private ip address. If it's not your network (meaning that your netadmin won't give you access to the router/firewall) you can just replace [www.mysite.dyndns.org]("http://www.mysite.dyndns.org") with mysite.localhost and use mysite as an alias. The easiest way to access your webserver from the inside, however, is to just enter localhost in the address bar if the server is on your machine, or enter the ip (10.10.0.2) in the address bar if it's not. The result will be the same no matter how you address it from your browser. You'll see the same thing everyone else sees.

Ed [/COLOR]
[/COLOR]

---

