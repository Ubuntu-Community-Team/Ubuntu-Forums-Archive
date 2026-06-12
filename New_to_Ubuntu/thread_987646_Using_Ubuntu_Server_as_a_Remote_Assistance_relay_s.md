---
title: "Using Ubuntu Server as a Remote Assistance relay server?"
date: 2008-11-19
forum: New to Ubuntu
---

### Post by nomad1970 on 2008-11-19
Don't know if this is possible, and haven't seen anything in my searches.

I have a linux server, combined with dyndns / ddclient installed so I have a pseudo static IP.

Is there any linux server software that is designed to allow two computers (running windows), to connect using the linux server to authenticate, and establish something similar to Windows Remote Assistance, or many of the other pay-for services out there?

Thanks!

---

### Post by sonofusion82 on 2008-11-19
if you just need to connect two windows machine, you can use hamachi but doesn't use your ubuntu server.

you can also install openvpn into the ubuntu server to create VPN among your windows machine so that they can use simple netmeeting sharing or remote desktop.

---

### Post by nomad1970 on 2008-11-19
Thanks for your reply.

I've looked at hamachi, seems to have too much client side configuration involved.

I'd like to be able to offer remote support the odd time to customers, without using windows remote assistance, or the very expensive alternatives out there.  

Just type in a fixed URL, possibly a simple client side plug-in - and connect.  In other words, exactly like the $150 / month type products one can buy.  

I'm probably missing something here, or maybe it just hasn't made it into open source as there isn't much demand.

---

### Post by aeiah on 2008-11-19
we use ultravnc at work for this purpose. clients who have logged into our support website can, when instructed and when we bother to launch ultravnc on our computer in listen mode, click a button on the website which downloads a small file, allowing a vnc connection between them and us to take place so we can see what mess they've got themselves into etc.

i guess you'll need that pseudo-static ip and input it into the script. im guessing ultravnc has this script somewhere as i doubt anyone in our office bothered to write it.

---

### Post by aeiah on 2008-11-19
ah yes, its on this page, called singleclick
[http://www.uvnc.com/addons/index.html](http://www.uvnc.com/addons/index.html)

---

### Post by nomad1970 on 2008-11-22
Well that was looking almost too good be true...

And it is - no linux version?

Thanks anyways!

---

