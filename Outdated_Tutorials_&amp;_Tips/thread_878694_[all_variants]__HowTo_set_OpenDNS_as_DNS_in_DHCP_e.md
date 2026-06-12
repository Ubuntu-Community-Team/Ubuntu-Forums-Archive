---
title: "[all variants]  HowTo set OpenDNS as DNS in DHCP env"
date: 2008-08-03
forum: Outdated Tutorials &amp; Tips
---

### Post by dentaku65 on 2008-08-03
Due to the recent vulnerability in the worldwide DNS
[http://www.vnunet.com/vnunet/news/2222592/first-dns-attacks-reported]("http://www.vnunet.com/vnunet/news/2222592/first-dns-attacks-reported")
[http://www.doxpara.com/?p=1189]("http://www.doxpara.com/?p=1189")
can be useful to change the DNS provided by your provider and use [OpenDNS]("http://opendns.org/") instead.

Here is described two ways to do it for DHCP users and without touching the router configuration (for users that have a static IP is pretty straightforward).
The first option change permanently the DNS
The second option change "when you need" the DNS

**Install a simple editor**
Install Scite to simplify and unify the editing for all *ubuntu distros.
```
sudo apt-get install scite
```

**1) Change DNS permanently**
Edit the dhcp configuration file:
```
sudo scite /etc/dhcp3/dhclient.conf
```
Add this line at the end and save the file:
```
prepend domain-name-servers 208.67.222.222, 208.67.220.220;
```

Reboot your machine.

Then try a non-existent url like:
[http://seeifthednsischangednow.com]("http://seeifthednsischangednow.com")
You should reach an OpenDNS response as search result in the OpenDNS home page... well you are using OpenDNS DNS.

**2 Change DNS when you need**
Create a file in your home:
```
scite ~/resolv.conf
```
Write the DNS IP of OpenDNS and save it:
```
nameserver 208.67.222.222
nameserver 208.67.220.220
```
Create a file under /usr/bin
```
sudo scite /usr/bin/dnsrenew
```
Write the following and save it
```
cp ~/resolv.conf /etc/resolv.conf
/etc/init.d/networking restart
```
Then chmod it to create an executable file:
```
sudo chmod +x /usr/bin/dnsrenew
```
Execute the script:
```
sudo dnsrenew
```
Then try a non-existent url like:
[http://seeifthednsischangednow.com]("http://seeifthednsischangednow.com")

Now you can use the DNS provided by OpenDNS till the next reboot.

**The Samba fix with OpenDNS (or external DNS)**
If you are using Samba (as supposed to be) and you are using the DNS of OpenDNS (or any external dns), you must change the configuration of Samba in order to be able to browse your LAN; so, edit your configuration file in this way:
```
sudo scite /etc/samba/smb.conf
```
and change the line of the *name resolver* section in this way:
```
name resolve order = lmhosts bcast wins host
```
Save and close the file
Then restart Samba:
```
sudo /etc/init.d/samba restart
```
Wait 10/15 minutes and you are able to browse your LAN with the new DNS.

I write this little HowTo just to use OpenDNS because I appreciate their service, I'm not involved in OpenDNS team.

---

### Post by Kaobear on 2008-08-03
Simple and very Concise, thank you.

---

