---
title: "[SOLVED] Antispyware/antikeylogger"
date: 2008-12-01
forum: New to Ubuntu
---

### Post by unf4b1x on 2008-12-01
I just installed ubuntu recently and I am totally new to it.  I just want to know what is the best anti-spywares/anti-keyloggers that I need to install further. Or do I need to?  Back when I use XP, although I got zonealarm for its firewall, I still got hit by keyloggers/spyware.  Now that im using ubuntu with firestarter and gufw, Im still kinda paranoid whenver firestarter turns red and tells me another hit has been detected.  Can anybody please tell me what should I be doing?

---

### Post by hyper_ch on 2008-12-01
I'd suggest you read the stickies in the Security section here in the forums for a beginning.

---

### Post by SunnyRabbiera on 2008-12-01
There is no spyware/ addware or windows registry keys to worry about in linux.
No viruses either, and firewall?
no problem :D
There is a firewall client preinstalled with linux though you need a front end for it.
But its easy enough to get

---

### Post by blackpaw on 2008-12-01
I agree: 
> I'd suggest you read the stickies in the Security section here in the forums for a beginning. 

However, people that use tools like zonealarm on Windows are being made paranoid.. I have been there, too.

Apparently this is a business model to sell more desktop firewalls. By reporting every little packet that is sent your way as a potential attack they make you feel you spend your money in a good way. Or should... 

On Usenet I once found a [firewall-FAQ]("http://www.iks-jena.de/mitarb/lutz/usenet/Firewall.en.html") that stated the following regarding desktop firewalls (like zonealarm):

> 
Users keep asking how they can protect themselves from being seen on the internet.. this is like owning a house on a street and complaining that people using a torch (nmap) can see their house even if sun, moon and street lights are off (having the firewall drop ICMP packets).

The answer these people want to hear is:
"There are nice, big stickers with an imprinting "This is not a house!" that your can stick to your windows. 
Free of charge and extra colorful are the ones from zonealarm."


(Desktop) Linux by default is pretty safe (meaning all ports to the outside world are closed).

The only thing you have to be aware of in Unix/Linux are: 
[LIST]
[*] malicious users trying to make you do stupid things (like "read mail - really fast" - a.k.a. rm -rf / )  
[*] rootkits - there are tools (ossec, rkhunter, chkrootkit, nessus) available that scan for them. Search the forums and repositories for them :)
[/LIST]


Have fun! :)

---

### Post by NewJack on 2008-12-01
> **blackpaw said:**
> I agree: 


However, people that use tools like zonealarm on Windows are being made paranoid.. I have been there, too.

Apparently this is a business model to sell more desktop firewalls. By reporting every little packet that is sent your way as a potential attack they make you feel you spend your money in a good way. Or should... 

On Usenet I once found a [firewall-FAQ]("http://www.iks-jena.de/mitarb/lutz/usenet/Firewall.en.html") that stated the following regarding desktop firewalls (like zonealarm):



(Desktop) Linux by default is pretty safe (meaning all ports to the outside world are closed).

The only thing you have to be aware of in Unix/Linux are: 
[LIST]
[*] malicious users trying to make you do stupid things (like "read mail - really fast" - a.k.a. rm -rf / )
[*] rootkits - there are tools (ossec, rkhunter, chkrootkit, nessus) available that scan for them. Search the forums and repositories for them :)
[/LIST]


Have fun! :)

+1 Excellent Post

---

### Post by lukjad on 2008-12-01
Thanks for the link blackpaw!

---

### Post by unf4b1x on 2008-12-01
Thank you all for answering my noob queries promptly.  I might do a lot of reading as well.

> On Usenet I once found a firewall-FAQ... 

*blackpaw thanks a lot for the link.

---

