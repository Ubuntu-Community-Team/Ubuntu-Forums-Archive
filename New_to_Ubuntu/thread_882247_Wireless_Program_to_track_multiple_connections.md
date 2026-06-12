---
title: "Wireless Program to track multiple connections"
date: 2008-08-06
forum: New to Ubuntu
---

### Post by TriSwords on 2008-08-06
I thought I read about a program earlier that allowed me to handle multiple wifi connections instead of one that it seems I can use only (or Im doing something wrong)

However I cant seem to find what I read on it. Any help? 

I have 3 different wifi connections I use (soon to be 4) and I am getting tired of having to put in each name and encryption every time I travel.

Thanks

---

### Post by nicedude on 2008-08-11
You could try wicd which is a replacement network manager for the standard one that Ubuntu uses, you will need to google it and then either add its source to your sources file or just find a deb package installer to download for it. Just a warning though when you install WICD it will or you will have to uninstall the standard network-manager ( if you add to sources and use synaptic it will uninstall it , if you use a deb package you will probably have to uninstall it but the deb installer will tell you what to remove if thats the case and you can use synaptic to do so then run the deb package again ). WICD does let you setup multiple access points complete with security info and then select from list which to connect to, so it might be just what you want.


Hope this helps

nicedude

---

### Post by ukripper on 2008-08-11
> **TriSwords said:**
> I thought I read about a program earlier that allowed me to handle multiple wifi connections instead of one that it seems I can use only (or Im doing something wrong)

However I cant seem to find what I read on it. Any help? 

I have 3 different wifi connections I use (soon to be 4) and I am getting tired of having to put in each name and encryption every time I travel.

Thanks

have you turned on roaming mode on network manager?

System-->Administration-->network manager and make sure it is using roaming mode.

---

