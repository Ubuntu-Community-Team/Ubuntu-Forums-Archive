---
title: "How do I turn IP address into names on private website"
date: 2013-02-27
forum: New to Ubuntu
---

### Post by Iwanttodj on 2013-02-27
Hello everybody,

I am looking for some advice.

Let me tell you what I am trying to achieve. 

I am using ubuntu server 12.04 and have created a website that will not be on the web. The idea is that people will be able to log on to a wifi hotspot that I have provided and log into my website only when on this hotspot. Wifi is not connected to the rest of the Internet. 

How can I use a name for the website instead of using an IP address? 

Any advice is welcome.

---

### Post by sandyd on 2013-02-27
> **Iwanttodj said:**
> Hello everybody,

I am looking for some advice.

Let me tell you what I am trying to achieve. 

I am using ubuntu server 12.04 and have created a website that will not be on the web. The idea is that people will be able to log on to a wifi hotspot that I have provided and log into my website only when on this hotspot. Wifi is not connected to the rest of the Internet. 

How can I use a name for the website instead of using an IP address? 

Any advice is welcome.
Do you have a configurable DNS Server (i.e. running dd-wrt/tomato/dnsmasq/etc) that is setup in the DHCP configuration?

If you do, you just manually add the name -> ip address mapping in the DNS Server that you are using.

Can you give us more detail about your configuration please?

Thanks!

---

