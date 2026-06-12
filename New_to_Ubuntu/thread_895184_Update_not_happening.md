---
title: "Update not happening"
date: 2008-08-19
forum: New to Ubuntu
---

### Post by veranda on 2008-08-19
Hi All, I'm new to Ubuntu/Linux so any help suggestions will need to be fairly detailed for me to follow them. When I start Ubuntu it tells me there are updates available...when I start the update Manager it tells me there are 199 updates available & the download size is 240.8 MB....when I click "Install Updates" the "Check & Install Update" buttons fade as if things are happening but nothing does happen. I've left it on for over 4 hours & even tried un-ticking all the available updates then selecting only one thinking lets do one at a time but still no joy.... this is where your help would be appreciated to solve this issue.... thanking you in anticipation.

---

### Post by iaculallad on 2008-08-19
> **veranda said:**
> Hi All, I'm new to Ubuntu/Linux so any help suggestions will need to be fairly detailed for me to follow them. When I start Ubuntu it tells me there are updates available...when I start the update Manager it tells me there are 199 updates available & the download size is 240.8 MB....when I click "Install Updates" the "Check & Install Update" buttons fade as if things are happening but nothing does happen. I've left it on for over 4 hours & even tried un-ticking all the available updates then selecting only one thinking lets do one at a time but still no joy.... this is where your help would be appreciated to solve this issue.... thanking you in anticipation.

Drop to your terminal: Application->Accessories->Terminal and type the code below:

```
sudo apt-get update && sudo apt-get upgrade
```

It's just normal that you won't see your typed characters echoed on screen. Just type your password and press Enter key.

---

### Post by veranda on 2008-08-19
Hey thanks for the quick response - that seems to be working....is this just a one off or will I need to do this with every update?

---

### Post by DougieFresh4U on 2008-08-19
You shouldn't have problems with update manager. I prefer the terminal for updating as I can see what is happening through out the update:
**sudo apt-get update **   then I
**sudo apt-get -f install** then
**sudo dpgk --configure -a** 
just to make sure all is neat and set to go

---

### Post by veranda on 2008-08-20
First part worked now there are 18 more updates which when using your instructions I get:
Reading Packing List .. Done
Building dependency tree
Reading state information ..Done
The following Packages have been kept back:
bind9-host dnsutils language -support - writing - en libbind9 - 30 libisccfg30
linux-generic linux - headers -generic linux image - generic
linux - restricted-modules - generic wine 
0 upgraded, 0 newly installed, 0 to remove and 10 not upgraded. 



Help

---

### Post by DougieFresh4U on 2008-08-20
> **veranda said:**
> First part worked now there are 18 more updates which when using your instructions I get:
Reading Packing List .. Done
Building dependency tree
Reading state information ..Done
The following Packages have been kept back:
bind9-host dnsutils language -support - writing - en libbind9 - 30 libisccfg30
linux-generic linux - headers -generic linux image - generic
linux - restricted-modules - generic wine 
0 upgraded, 0 newly installed, 0 to remove and 10 not upgraded. 



Help

Tell me, what did you put into terminal

---

### Post by veranda on 2008-08-20
First I tried using the update manager - nothing hapened
Then tried: sudo apt-get update && sudo apt-get upgrade
that's when I got the above message & then tried your suggestion but got no further than the second command & then more or less the same message

---

### Post by DougieFresh4U on 2008-08-20
Ok, lets try this, Iwill try to help you save if I can 
in the terminal -open new term- 
**sudo apt-get update**   then lets try 
**sudo apt-get dist-upgrade**

---

### Post by veranda on 2008-08-20
Ok that worked - can you tell me why the update manager is not working properly - I would much prefer to use it (I've seen a some negative comment about using sudo apt-get dist-upgrade & what it does or may not do), basically I'm looking for the simplest & safest way to use a computer, but hey thanks for your help, much appreciated.

---

### Post by t0p on 2008-08-20
> **veranda said:**
> Ok that worked - can you tell me why the update manager is not working properly - I would much prefer to use it (I've seen a some negative comment about using sudo apt-get dist-upgrade & what it does or may not do), basically I'm looking for the simplest & safest way to use a computer, but hey thanks for your help, much appreciated.

I'd be interested to know what "negative comment" you've heard about apt-get and why you think apt-get dist-upgrade is unsafe.

---

### Post by veranda on 2008-08-20
> I'd be interested to know what "negative comment" you've heard about apt-get and why you think apt-get dist-upgrade is unsafe.

For your "Interest" TOP


[http://www.oreillynet.com/onlamp/blog/2006/10/aptget_distupgrade_broken_goin.html](http://www.oreillynet.com/onlamp/blog/2006/10/aptget_distupgrade_broken_goin.html)

Anyway, instead of querying my comment, how about making yourself useful and answer my question as to why the Update Manager's not working the way it should!!

---

