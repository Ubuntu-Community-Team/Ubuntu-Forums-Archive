---
title: "DNS Server EHCP"
date: 2008-09-12
forum: New to Ubuntu
---

### Post by zuber786 on 2008-09-12
DNS Server 

--------------------------------------------------------------------------------

hi 
I first want to thank EHCP nice work

I need some help at this part
I am running my server on router i have port 80 & 21 over 
I can view my page both by going to 
[http://localhost](http://localhost)
[http://192.168.2.XX](http://192.168.2.XX)
[http://BYMYIPADDRESS](http://BYMYIPADDRESS) 
but this takes me to my the control panel

I added my domain name

now when I go to my domaiin website where I registered my domain
namecheap.com when I try to transfter dns to webhost
what should I type there.
if I type my ip address It doesn't let me type my address there.


this is what it says on the page where I have option to add dns server name


"Please enter DNS name only (ex: ns1.mydomain.com). Please don't enter IP
addresses. You can enter up to five name servers. It is advisable to enter atleast
two nameservers for a domain. Please note that it will take up to 24 hours for
the changes to take effect. "

please help me
thank you

---

### Post by dhtseany on 2008-09-12
Hi,
If I'm not mistaken I believe you need to have namecheap manually set it for you. I know that if you want a subdomain to forward to "http://<subdomain>.domain.org" you need to have them create a special MX record for that. Try contacting their tech support and ask them.

Hope that helped,
Sean

---

### Post by halitech on 2008-09-12
if you are hosting the site yourself, you can use Zone Edit for a DNS server and then point namecheaps dns server to zone edits info

---

### Post by zuber786 on 2008-09-12
I made the server name through my domain regratrant control panel
ns1.mydomain.com = my ip
ns2.mydomain.com = my ip

I went to transfer DNS TO WEBSITE
here I entered
ns1.mydomain.com
ns2.mydomain.com

now it is showing me
page cannot be displyed

---

### Post by halitech on 2008-09-12
are you running a DNS server on your computer that all the other DNS servers are aware of?

---

### Post by zuber786 on 2008-09-12
I am hostng my site & my hosting control panel on my computer.

DNS Server, I made on my namecheap.com where I registered my domain, 
there I forwarded my ip and made my dns server
like I showed before
ns1.mydomain.com = myip
ns2.mydomain.com = myip 

ip for both ns1 & ns2 are same as my ip om my server

---

### Post by dhtseany on 2008-09-12
Online networking isn't my strong point, but I don't think the way that you've tried would work. I'm not trying to beat a dead horse but I really think you need to contact namecheap's tech support for this one. 

One more thing: Verify that you can see the page from another computer on your network by using the [http://192.x.x.x](http://192.x.x.x).

Sean

---

### Post by zuber786 on 2008-09-13
ya 
I can view my page using my ip address, but only control panel
I even login to my ftp and only view folder for only domain for I made account.
but I can view files in ftp [ftp://myipaddress.com/vhosts/mydomain.com/httpsdos](ftp://myipaddress.com/vhosts/mydomain.com/httpsdos) I can view them here throught ftp.
, but not in in [http://mydomain.com](http://mydomain.com).

---

### Post by dhtseany on 2008-09-13
I think that now your starting to get into the LAMP configuration. I think you need to edit the config file for Apache and point it to the directory where you are storing your web files. 

Check out this tutorial:
[http://minitutorials.com/apache/apache_222_3.shtml](http://minitutorials.com/apache/apache_222_3.shtml)

(Sorry if it doesn't give you specifics on what you need to do but I think it'll help you get a better understanding of the direction you need to take)

Peace
Sean

---

### Post by zuber786 on 2008-09-13
I am using 
EHCP - Easy Hosting Control Panel for Ubuntu
Which did all the work for me, I don't have to do anything, only thing my setup is wrong at is at DNS Server which is not understood by my domain registerant.

---

### Post by halitech on 2008-09-14
Unless you have registered your computer with the organization that looks after DNS Servers, the information about your domain isn't being sent to anyone so trying to bring it up by domain name isn't going to work. You need to have legitimite DNS servers in order to have your domain information propagate over the internet.

take a read here: [http://www.howstuffworks.com/dns.htm](http://www.howstuffworks.com/dns.htm)

[http://en.wikipedia.org/wiki/Domain_name_system](http://en.wikipedia.org/wiki/Domain_name_system)

---

### Post by bvidinli on 2008-11-24
hi,
as halitech said,
you need to register your domain in a domain seller, then redirect your domain to your server as dns..

you need to register your server as dns server in your domain seller.
domain seller's usually have sections like register dns.

Go to register dns, 
enter ns1.yourdomain.com to name, and your external/real server ip as dns ip.
you may use same ip for both ns1.yourdomain.com and ns2.yourdomain.com

Unfortunately, some domain sellers does not allow same ip for ns1 and ns2. In this case, you need either a secondary ip for your server, or you need to port your domain to another domain seller/registrar.. 

have a look at relevant pages too:
[http://www.ehcp.net/?q=node/167](http://www.ehcp.net/?q=node/167)
[http://www.ehcp.net/?q=node/106](http://www.ehcp.net/?q=node/106)
[http://www.ehcp.net/?q=node/104](http://www.ehcp.net/?q=node/104)
[http://ubuntuforums.org/forumdisplay.php?f=180](http://ubuntuforums.org/forumdisplay.php?f=180)

---

