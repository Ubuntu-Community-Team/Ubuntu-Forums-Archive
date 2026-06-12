---
title: "Using 3G phones as a modem - Nokia N95 or LG 'the secret'?"
date: 2008-08-15
forum: New to Ubuntu
---

### Post by klaasvanschelven on 2008-08-15
I'm **considering buying a phone** with email & browsing capabilities and would like to make sure it's a useful addition to my Ubuntu Linux system as well. "Ask before buy" has served me well in the past and I'd like to reward systembuilders that support the Open Source movement in terms of compatibility by buying their stuff. 

In particular I'd like to **use my phone as a modem** and **transfer files** from and to my Ubuntu system(s). Syncing of contacts is a nice extra but no priority.

I'm looking at two models in particular:
* the Nokia N95
* the LG 'the secret'.
Remarks on other models (both positive and negative) are welcome as well.

My location is the Netherlands. Vodaphone is one of the networks I'm considering. Again, info on other networks in interesting as well.

Any sharing of experiences on any of the above is very welcome. Does this (especially using the phone as a modem) work out of the box? Where are the guides?
I've run across a couple of guides but they seem ages old and not for any of the above models. Are they cross-phone applicable?

old/other models:
[http://mybroadband.co.za/vb/showthread.php/?t=21726](http://mybroadband.co.za/vb/showthread.php/?t=21726)
[http://www.inorp.com/blog/2007/03/13/ubuntu-guide-to-using-hsdpa-usb-modem-huawei-e220-with-the-tre-network/](http://www.inorp.com/blog/2007/03/13/ubuntu-guide-to-using-hsdpa-usb-modem-huawei-e220-with-the-tre-network/)
[http://www.linux.ie/articles/tutorials/threeirelandUSBmodem.php](http://www.linux.ie/articles/tutorials/threeirelandUSBmodem.php)

I have Ubuntu 7.10 Gibbon installed currently.

regards,
Klaas

---

### Post by t0p on 2008-08-15
In my sig is a link to a tutorial I wrote for using a cellphone as a modem.  At the end of the tutorial is a bit relevant to using a 3G phone.  I use a Sony Ericsson K800i.  I don't know if it's the same for the models you want to use.

---

### Post by Initsil on 2008-08-15
I know the iPhone used to have an app called Netshare. Where you plugged it into your computer, then it used your iPhone 3G as a network device.

---

### Post by seanreynoldscs on 2008-08-26
Hey guys, 
I have Netshare on my iPhone. I have been able to get the wifi linking and proxy to work on both OSX and Vista; however I cant seem to get it to work on Ubuntu.

Essentially all that is needed is: 
Create a WIFI Access point for adhoc connections
Set the computers IP address manually.

Beyond that I was hoping that Ubuntu had a nice way of rerouting all network traffic through a proxy without a program like Proxifier.

I'm pretty new to Ubuntu, I have an Atheros wifi card and even to get it to work I had to use Ndiswrapper. Ive looked into madwifi but I couldnt seem to get it to work last night. Any Ideas?

---

### Post by NoMax2 on 2008-09-15
Hello,

 I have an iPhone 3G and NetShare.  I want to use my iPhone as a modem.  I set up an ad-hoc wireless network between my Ubuntu PC and my iPhone.  When it's up and running I can ping my iPhone address from my Ubuntu PC.  I then go into Firefox and specify the iPhone IP as my SOCKS 5 proxy.

 Now the problem. . .I have no DNS resolution, so if I enter "http://www.google.com" nothing happens...I need to enter "http://64.233.161.99" to get the Google page. Not too useful as-is!!!

 I tried adding some public DNS server addresses in /etc/resolv.conf, no effect.  I tried going into preferences and specifying the SOCKS address there, didn't help.  I also tried to edit the advanced Firefox settings (through "about:config") telling it to use remote DNS through SOCKS, not even that helped :-(

 I need a solution that will pass all traffic through the iPhone's SOCKS proxy, and give me DNS. . .any clues as to what I can do?  

 Thanks in advance for any help you can give me.

NM2

---

### Post by seanreynoldscs on 2008-09-16
I ended up buying a mac. I have a macbook air now. If you like linux, but get tired of things not working, try osx. You can setup alot of the same unix commands and the hardware and drivers all work.

Inside of osx, you can get remote dns. You can enter the iphone ip address into the dns under the network preferences, or in proxifier you can set the dns to be passed through.

OSX is like linux, except it works. I spend less time trying to get the little things to work, and more time doing the impossible! I love it!

---

### Post by Mornedhel on 2008-09-16
> **seanreynoldscs said:**
> OSX is like linux, except it works.


And except it comes with a price tag. Attached to both the OS and the hardware you have to run it on.

---

### Post by frederik.nnaji on 2008-10-26
@seanreynoldscs
point definitely taken, but why u gotta go offtopic like this?
not quite constructive in the context of what this forum stands for..

---

