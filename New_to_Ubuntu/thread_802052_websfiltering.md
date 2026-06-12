---
title: "websfiltering"
date: 2008-05-21
forum: New to Ubuntu
---

### Post by ibizatunes on 2008-05-21
Is there a nice easy way of install and managing webfiltering on a ubuntu machine? I trying to win over a few peope to use ubuntu and they want to be able to webfilter on each pc but it must be easy to use!!

---

### Post by PartisanEntity on 2008-05-21
In the repo you should find the 'webstrict' package which can help you filter web content.

---

### Post by hyper_ch on 2008-05-21
what do you mean by "webfiltering"?

---

### Post by ibizatunes on 2008-05-21
basicly i want to create a small network, with about 8 machines, basiclly anyone can log on, within the company for unresticted internet access! but unresticted within a reasonable level! ie no porn, etc etc

---

### Post by hyper_ch on 2008-05-21
hmmmm, maybe setting up a proxy/gateway with Squid would be an option.

---

### Post by PinkFloyd102489 on 2008-05-21
There's a guide in Tutorials that uses TinyProxy and Dansguardian. Set a machine up with these on it then point the web browsers of the machines to it.

---

### Post by ibizatunes on 2008-05-21
I would like to set up a squid proxy! but we have 8 old workstation, and no spare servers, and the bosses want 8 pc for this project so im limited, so i need to webfiltering on the PC on itself!

---

### Post by ushills on 2008-05-21
Try Procon latte the firefox add-on, this allows you to filter each pc. [http://www.ushills.co.uk/2008/04/procon-latte-content-filter.html](http://www.ushills.co.uk/2008/04/procon-latte-content-filter.html)

Alternatively, try opendns again you can content filter each pc via the open dns server.

You can also filter each pc with dansguardian as a stand-alone setup.  [http://www.ushills.co.uk/2008/04/setup-dansguardian.html](http://www.ushills.co.uk/2008/04/setup-dansguardian.html)

---

### Post by ibizatunes on 2008-05-21
I would like to set up a squid proxy! but we have 8 old workstation, and no spare servers, and the bosses want 8 pc for this project so im limited, so i need to webfiltering on the PC on itself!

---

### Post by ushills on 2008-05-21
With your setup i would suggest [http://www.opendns.com]("http://www.opendns.com") you can get reports on sites visited and most routers will allow you to set dns on them so you don't need to configure each pc.

Start here [https://www.opendns.com/start]("https://www.opendns.com/start")

---

### Post by hyper_ch on 2008-05-21
however you can still manually set dns servers on each machine... but I guess most people won't know how.

---

### Post by ushills on 2008-05-21
you could always change the permissions on /etc/resolv.conf so that they are read-only and only editable by sudoers this would prevent local changes to the dns servers used.

---

