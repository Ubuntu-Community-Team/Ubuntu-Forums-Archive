---
title: "cannot connect to repositories"
date: 2006-05-06
forum: Repositories &amp; Backports
---

### Post by Zo|oZ on 2006-05-06
I'm trying to run Synaptic Package Manager. I keep getting this error:

Err [http://archive.ubuntu.com:80](http://archive.ubuntu.com:80) (1.0.0.0), connection timed out

same error for all sources listed.

---

### Post by Zo|oZ on 2006-05-06
[QUOTE=Zo|oZ]I'm trying to run Synaptic Package Manager. I keep getting this error:

Err [http://archive.ubuntu.com:80](http://archive.ubuntu.com:80) (1.0.0.0), connection timed out

same error for all sources listed.[/QUOTE]


Well, my problem really seems to be that DNS isn't configured properly. I'll take this to absolute beginners and ask there.

---

### Post by asingh on 2006-05-16
Most probably, your system uses a proxy. If that is so, follow these steps:
(Steps 1-2 are required evenif your system is not under proxy. Hopefully you have already done it. Here,  your_proxy:the_port is that you entered in firefox connection, for example:
proxy.iitc.ernet.in:8080)

1. Go to the page below and auto-generate the sources.list by choosing many types of sources:
[http://www.ubuntulinux.nl/source-o-matic](http://www.ubuntulinux.nl/source-o-matic)
Replace the lines with (or comment them and Copy-paste) the generated lines to your /etc/apt/sources.list 

2. If you get errors about missing keys, lookup the key in this file and run these commands (replace KEY with the key number given in the commented lines of /etc/apt/sources.list)
 gpg --keyserver subkeys.pgp.net --recv KEY
 gpg --export --armor KEY | sudo apt-key add -

3. Fix apt-get to work under proxy:
sudo gedit /etc/apt/apt.conf
and add the following lines to that (might be empty) file:
ACQUIRE {http::proxy "http://your_proxy:port/"}
Save and exit gedit.

4. Fix proxy for wget:
sudo gedit /etc/wgetrc
Check and correct the following lines there:
# You can set the default proxies for Wget to use for http and ftp.
# They will override the value in the environment.
http_proxy = [http://your_proxy:port/](http://your_proxy:port/)
ftp_proxy = [http://your_proxy:port/](http://your_proxy:port/)
# If you do not want to use proxy at all, set this to off.
use_proxy = on
Save and exit gedit

5. Your system should work for managing packages. Use:
sudo apt-get update
sudo apt-get dist-upgrade

6. Use synaptic package manager from System->Administration->Synaptic Package Manager
to install packages.

---

### Post by asingh on 2006-05-16
[QUOTE=Zo|oZ]I'm trying to run Synaptic Package Manager. I keep getting this error:

Err [http://archive.ubuntu.com:80](http://archive.ubuntu.com:80) (1.0.0.0), connection timed out

same error for all sources listed.[/QUOTE]

[QUOTE=asingh] Your system does not connect to Ubuntu packages (repositories). Most probably, your system uses a proxy. If that is so, follow these steps:
(Steps 1-2 are required evenif your system is not under proxy. Hopefully you have already done it. Here,  your_proxy:the_port is that you entered in firefox connection, for example:
proxy.iitc.ernet.in:8080)

1. Go to the page below and auto-generate the sources.list by choosing many types of sources:
[http://www.ubuntulinux.nl/source-o-matic](http://www.ubuntulinux.nl/source-o-matic)
Replace the lines with (or comment them and Copy-paste) the generated lines to your /etc/apt/sources.list 

2. If you get errors about missing keys, lookup the key in this file and run these commands (replace KEY with the key number given in the commented lines of /etc/apt/sources.list)
 gpg --keyserver subkeys.pgp.net --recv KEY
 gpg --export --armor KEY | sudo apt-key add -

3. Fix apt-get to work under proxy:
sudo gedit /etc/apt/apt.conf
and add the following lines to that (might be empty) file:
ACQUIRE {http::proxy "http://your_proxy:port/"}
Save and exit gedit.

4. Fix proxy for wget:
sudo gedit /etc/wgetrc
Check and correct the following lines there:
# You can set the default proxies for Wget to use for http and ftp.
# They will override the value in the environment.
http_proxy = [http://your_proxy:port/](http://your_proxy:port/)
ftp_proxy = [http://your_proxy:port/](http://your_proxy:port/)
# If you do not want to use proxy at all, set this to off.
use_proxy = on
Save and exit gedit

5. Your system should work for managing packages. Use:
sudo apt-get update
sudo apt-get dist-upgrade

6. Use synaptic package manager from System->Administration->Synaptic Package Manager
to install packages.[/QUOTE]
 
This should do the job.

---

### Post by mikesull on 2006-05-22
I've had the same problem. From what I've gathered its a dns problem when using a router or modem/router. Even if ipv6 is disabled in firefox and from the entire system it doesn't help. I've found this bug in Fedora 4 as well. IF YOU DON'T USE A ROUTER THIS WILL PROBABLY NOT APPLY TO YOU!
You will be able to tell this is an dns issue by being able to ping any numerical IP address, but not a alphabetical address like "www.yahoo.com". Although even if you can ping some alpahbetical adresses it wouldn't hurt to try.
I have an Actiontec DSL gateway modem/router, and after trying over a dozen different things in different ordrers I found and easy fix. 
Log into your router through a web browser, mine is 192.168.0.1. Find what your dns server IP's are (on my router there under "status"). Copy these 2 adresses down. Then go to System->Administration->Networking, or network-admin in the comand line. Click on the DNS tab and enter the DNS server addresses you got from your router are on the top of the list.

---

### Post by so_simple on 2006-06-03
i have the same problem and i cant resolve it! anybody can help me?!?

---

### Post by JaqHama on 2006-06-04
Not sure how much mileage you'll get out of this.

I recently hooked up to DSL and while I could browse the web intermittently (and that was the frustrating part) I couldn't connect to the repositories. So I turned off IPV6 (my DSL modem couldn't handle it - DLink-502T)

info here [http://www.ubuntuforums.org/showthread.php?t=187534](http://www.ubuntuforums.org/showthread.php?t=187534)

I was up and running after turning off IPV6 (also turned off in FireFox) then you can either reboot or issue

sudo ifdown eth0 (if eth0 is your NIC)
sudo ifup eth0

---

### Post by Gergie on 2006-06-10
I had the same problem, using a D-Link DSL-502T modem. Obviously this modem has problems with DNS. The following solved the problem for me:
Open modem config in any browser (address 10.1.1.1), goto "DNS" and choose "Disable DNS Relay". Now add any DNS addresses to your local /etc/resolver.conf, or simply via the GUI in "System Settings" -> "Network Settings" -> "Domain Name System".
If you don't disable the modem's DNS relay, the local settings will be reset by the modem via DHCP.
Good luck!

---

