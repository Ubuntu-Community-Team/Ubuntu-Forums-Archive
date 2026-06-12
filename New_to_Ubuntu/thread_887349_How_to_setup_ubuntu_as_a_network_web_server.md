---
title: "How to setup ubuntu as a network web server?"
date: 2008-08-12
forum: New to Ubuntu
---

### Post by markmontereal on 2008-08-12
Hi! I am new in this forum and I would like to learn more about Ubuntu.

We are a small team of web developers and I would like to consider Ubuntu as a web server of a network that comprises of Windows workstations for our web development projects.

What I want to achieve is to make Ubuntu act like an internal web hosting which will host our website projects. For example, a website for Client A and Client B will be hosted in the web server and will be accessible throughout the network via [http://lan.clienta.com](http://lan.clienta.com) and [http://lan.clientb.com](http://lan.clientb.com) respectively.

Maybe this task includes Virtual Host and DNS, but I don't know how to do it. I would like to use Ubuntu to this kind of platform.

Hope you could help me, thanks.

---

### Post by fahadsadah on 2008-08-12
If you have a DNS server, great! Otherwise, looks like you'll be doing this from Ubuntu.

```
sudo aptitude install bind
```

Webserver? Done:
```
sudo aptitude install apache2
```

FTP?
```
sudo aptitude install proftpd
```
[Configuring BIND]("http://linux-sxs.org/internet_serving/dns.html")
[Configuring Apache]("http://bytes.com/serveradministration/webservers/apache/theapachewebserver/page1.html")
[Configuring proftpd]("http://www.castaglia.org/proftpd/doc/contrib/ProFTPD-mini-HOWTO-ConfigFile.html")

---

### Post by cdtech on 2008-08-12
This is the way I set up my server:
[http://www.tweako.com/the_perfect_lamp_setup_ubuntu_hardy_heron_ubuntu_8_04_lts_server](http://www.tweako.com/the_perfect_lamp_setup_ubuntu_hardy_heron_ubuntu_8_04_lts_server)

Hope this helps........

---

### Post by Rossco_ on 2008-08-12
I'd personally recommend XAMPP ([Link here]("http://www.apachefriends.org/en/xampp.html"))

It gets all of the features you might need for running a server in a simple install package. It may mean in future you need to change some of the commands people will give you, but it's brilliant if you just want the "No hassle" option.

---

### Post by hyper_ch on 2008-08-12
if you want to host multiple websites at once you may want to have a look at [http://www.howtoforge.com/perfect-server-ubuntu8.04-lts](http://www.howtoforge.com/perfect-server-ubuntu8.04-lts) with ISPConfig setup.

Then you would also need either the hosts file pointing an entry to the server for the according domains OR have your dns server resolve them to your server.

---

### Post by markmontereal on 2008-08-12
Thank you guys, it's a great help. I will start reading those articles to setup our network.

---

### Post by jonabyte on 2008-08-12
when you are ready do a search on virtual host on this forum, there are a lot of good posts regarding it.

---

### Post by stoneybroke on 2008-08-12
If you are also creating websites try Typo3 at [www.typo3.org](www.typo3.org) its a free web design program like dream weaver in windows.

hyper_ch Great link that you posted thanks that was just what I needed.

---

### Post by hyper_ch on 2008-08-12
typo3 is a very advanced CMS program... not a web design software like Dreamweaver...

---

### Post by stoneybroke on 2008-08-12
Typo3 is web design software go read documents same as dreamweaver both do CMS I know used both

---

### Post by hyper_ch on 2008-08-12
[http://typo3.com/](http://typo3.com/)
> TYPO3 is a free Open Source content management system for enterprise purposes on the web and in intranets.

---

### Post by markmontereal on 2008-08-12
I have another question. How can I make my Windows workstations to search for dns record (host/domain) in Ubuntu server and can still connect to the internet?

For example, my Windows workstations can browse lan.clienta.com website which is in my Ubuntu server and at the same time the Windows workstation can browse the Internet.

Thank You.

---

### Post by ds[de] on 2008-08-13
Setting the "dns-server"-option (in network settings in Windows) to the IP-Address to your ubuntu server should do the trick.

bind should be configured to return the IP-Address of the machine its running on for requests like 
lan.clienta.com
and consult your providers dns server for addresses that are not locally defined. 

Otherwise, you could just edit the 'hosts'-file on your windows machines to link lan.clientX.com to the ubuntu machine.
Then you wouldn't have to install bind and your current internet settings may remain untouched.

Regards,
ds[de]

---

### Post by markmontereal on 2008-08-14
> **'ds[de] said:**
> Setting the "dns-server"-option (in network settings in Windows) to the IP-Address to your ubuntu server should do the trick.

bind should be configured to return the IP-Address of the machine its running on for requests like 
lan.clienta.com
and consult your providers dns server for addresses that are not locally defined. 

Otherwise, you could just edit the 'hosts'-file on your windows machines to link lan.clientX.com to the ubuntu machine.
Then you wouldn't have to install bind and your current internet settings may remain untouched.

Regards,
ds[de]

oh is that so? it's so techie. Thanks a lot.

---

