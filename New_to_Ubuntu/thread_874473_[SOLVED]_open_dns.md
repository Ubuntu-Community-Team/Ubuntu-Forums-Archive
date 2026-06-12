---
title: "[SOLVED] open dns"
date: 2008-07-30
forum: New to Ubuntu
---

### Post by matchstich on 2008-07-30
i went to open dns

[https://www.opendns.com/start?device=ubuntu](https://www.opendns.com/start?device=ubuntu)


followed all the commands, cept for the last one i got

 sudo ifdown eth0 && sudo ifup eth0 
ifdown: interface eth0 not configured
Ignoring unknown interface eth0=eth0.


the last line is

You may be required to change eth0 to your own network device's name if it uses a non-standard name.

any one know what i need to do next?  do not understand the "eth0 not configured" , i connect using a cable modem.

thanks

---

### Post by jwaiwit on 2008-07-30
> **matchstich said:**
> i went to open dns

[https://www.opendns.com/start?device=ubuntu](https://www.opendns.com/start?device=ubuntu)


followed all the commands, cept for the last one i got

 sudo ifdown eth0 && sudo ifup eth0 
ifdown: interface eth0 not configured
Ignoring unknown interface eth0=eth0.


the last line is

You may be required to change eth0 to your own network device's name if it uses a non-standard name.

any one know what i need to do next?  do not understand the "eth0 not configured" , i connect using a cable modem.

thanks

Those command is for bring down and up following iface in /etc/network/interfaces.

When i have to complete this step I just restart system. 
Hope this help.

---

### Post by roquefilipe on 2008-07-30
that line is to restart you connection. the interface name may be different. Use "ifconfig" to list all available interfaces. Usually wired ones will be "ethX" and wireless ones will be "wlanX", but its not strict. 

As I said that line is to restart your connection, so restart your OS should simply work.

---

### Post by lisati on 2008-07-30
If you're using a wired network, it's possible that either Ubuntu isn't recognizing your connection or that you need to use something other than eth0

If you're using wired, type in ```
ifconfig
``` at the terminal and look for the entry for your wired network. If it's connected and functioning there should be an entry for a connection identified as ethernet.

---

### Post by Rakathan on 2008-07-30
Go to System > Administration > Network

You'll see whatever ethernet connections you have listed...I've got eth0 on mine (the onboard ethernet), but I think I'm actually using eth1 (PCI ethernet card).  Try looking at the names of those connections and substitute them in.

---

### Post by matchstich on 2008-07-30
ok, under general



mine say wired connections

then i open properties


enable roaming mode is checked

the rest is blank

 


and point to point  

which is disabled.

thanks

---

### Post by dentaku65 on 2008-07-30
My :) sticky for OpenDns here:

[http://ubuntuforums.org/showthread.php?t=872500](http://ubuntuforums.org/showthread.php?t=872500)

---

### Post by matchstich on 2008-07-31
ok, i opened the terminal and i saw 

#prepend domain-name-servers 208.67.222.222, 208.67.220.220;

it was already there.  do i need to reemove the #?

thanks

---

### Post by dentaku65 on 2008-07-31
> **matchstich said:**
> ok, i opened the terminal and i saw 

#prepend domain-name-servers 208.67.222.222, 208.67.220.220;

it was already there.  do i need to reemove the #?

thanks

yes :)

---

### Post by matchstich on 2008-07-31
ok, will have to research how to do  that, 


thanks

---

### Post by Joeb454 on 2008-07-31
I got that error when I tried to do ifdown/up etc.

Just go to [http://www.opendns.com](http://www.opendns.com) and it will tell you if you're using it near the top of the page :)

---

### Post by matchstich on 2008-08-05
i opened network. clicked on dns, put in opendns addresses.

removed the # and put in the dns addresse

in the line prepend domain-name-servers 208.67.222.222, 208.67.220.220;

cept it keeps switching back to  to my isp.

thanks

heck, i went back to the prepend line and the   ;   was not not on the end.   put it in.

maybe that will fix it.

---

