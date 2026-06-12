---
title: "Do I Need A Mail Server in a mixed Windows/Linux environment?"
date: 2008-08-10
forum: New to Ubuntu
---

### Post by DLLong on 2008-08-10
I've added a Ubuntu server to my windows active directory to allow me to run a development server for ZenCart that is natively Linux.   The DNS, DHCP, etc. are all taken care of by the Windows servers.  I've gotten everything working for ZenCart but am now tackling sending email from the website which currently sits on the Ubuntu server. On the Windows side, website email is sent from the websites to my ISP where their SMTP server takes care of delivery.    Neither of my Windows servers are set up as SMTP servers since it is all handled by the ISP.

My question is do I have to set anything up on the Ubuntu server for the website it is hosting to send mail?  I will still route the email through my ISP's SMTP server but while the Windows servers don't require anything, I'm not sure about Linux.  I don't think that it makes any difference to my Ubuntu server that all it's internet traffic is being routed through a gateway server, right?

---

### Post by hyper_ch on 2008-08-11
you will have to setup a MTA (and probably relay it through the windows mail server) in order to send emails.

---

