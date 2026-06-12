---
title: "Proxy Firewall Router Server IDS FTP"
date: 2008-08-30
forum: New to Ubuntu
---

### Post by marufaberlin on 2008-08-30
Hi,

I have just installed a Voyage Linux ([http://linux.voyage.hk/](http://linux.voyage.hk/)) on my ALIX.2c3 Mainboard ([http://www.pcengines.ch/alix.htm](http://www.pcengines.ch/alix.htm)). Voyage is Debian derivate (so I don't feel bad about posting here).

It works great, I have an SSH access to the shell. I am using eth0 for my internal network and eth1 is connected to the internet router. Now, my questions are:

1. How can I configure Squid to act as a proxy on eth0 and fetch pages on eth1? I have no experience whatsoever when it comes to Squid.

2. How can I install and configure an IDS and Firewall?

3. I have already installed a LAMPP Webserver, but it only listens on eth0. How can I make it visible to the outside?

4. How can I set up the system to work as a DHCP server on eth0?

5. How can I set up FTP and fish: access?

6. How can I set up subdomains in Apache and have the home directories of the users be the corresponding htdocs folders?
etc. /home/marufaberlin/index.php = [http://marufaberlin.mydomain.org/index.php](http://marufaberlin.mydomain.org/index.php)

I would be grateful for any support.

---

### Post by jamesrfla on 2008-08-30
I do believe webmin supports squid. Wedmin allows you to configure your squid server through the web browser. To get it go to ```
sudo apt-get install webmin
``` Then to access it put this in your web browser [https://localhost:10000/](https://localhost:10000/) Then log in with your same user name and password as you do when you log in to Ubuntu. Then go to the networking tab on the left and click squid. You also should be able to configure DHCP from webmin too. The firewall is automatically configured if you have iptables. Hope this helps. :)

---

### Post by marufaberlin on 2008-08-30
Which debian repos do i have to enable to get webmin?

---

### Post by marufaberlin on 2008-08-30
It doesnt work.
```

$ sudo apt-get install webmin 
Reading package lists... Done
Building dependency tree... Done
Package webmin is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package webmin has no installation candidate

```

---

### Post by jamesrfla on 2008-08-30
I forgot you couldn't do it that way. Go hear and download it [http://sourceforge.net/project/downloading.php?groupname=webadmin&filename=webmin_1.430_all.deb&use_mirror=voxel](http://sourceforge.net/project/downloading.php?groupname=webadmin&filename=webmin_1.430_all.deb&use_mirror=voxel)

---

### Post by marufaberlin on 2008-08-30
Ok, Thanks for the link. I found it too, looking in Google, but now I am confronted with the next problems: How can I configure the proxy server to route traffic to it from the internal network (eth0, 192.168.0.1/24) to the internet router (eth1, 192.168.1.1/24)?
Do I have to use subnets for that?

Thanx in advance,

marufaberlin

---

### Post by marufaberlin on 2008-08-30
Ok, so I set up the services as far as I could, but if I try to start Squid, I get the following error message:

```


[B]Failed to start Squid : 2008/08/30 19:39:17| parseConfigFile: line 4351 unrecognized: 'httpd_accel_with_proxy on'
2008/08/30 19:39:17| parseConfigFile: line 4352 unrecognized: 'httpd_accel_uses_host_header off'
2008/08/30 19:39:17| parseConfigFile: line 4353 unrecognized: 'httpd_accel_single_host off'
[/B]

 
```

What's wrong?

Thanx in advance,

marufaberlin

---

### Post by marufaberlin on 2008-09-01
Bump

---

### Post by marufaberlin on 2008-09-01
Nobody helps me :frown:

---

### Post by marufaberlin on 2008-09-02
bump

---

### Post by marufaberlin on 2008-10-01
HELP!!!](*,)#-o

---

### Post by marufaberlin on 2008-10-01
well.... can someone at least tell me how to implement this:

I have 2 networks:
192.168.0.1/24
192.168.1.1/24

the network 192.168.1.1/24 is connected to the internet through a router.
the both networks are attached to different ethernet ports of a computer.
How can I use the internet from 192.168.0.1/24?

Do I have to set a route?
And how do I do that?

:confused:

---

