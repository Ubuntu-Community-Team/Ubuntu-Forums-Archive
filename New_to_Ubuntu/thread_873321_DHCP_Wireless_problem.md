---
title: "DHCP Wireless problem"
date: 2008-07-28
forum: New to Ubuntu
---

### Post by bshrum on 2008-07-28
First off i have been reading through these forums like a madman trying to find an answer and have now resorted to asking for help.  My Wireless card works SOMETIMES in ubuntu meaning it will work for long periods of time, but after a reboot it wont work. Iwconfig recognizes my card, i use ndiswrapper for the drivers and everything is great when i can get a DHCP address but i feel like i have tried everything to no avail.  I'm on my mac now so i cant post any code or output from iwconfig but any suggestions would be great.  Thanks in advance and Ubuntu is the greates OS i have ever booted into.

---

### Post by hubie on 2008-07-29
How is the wireless set up?  Open, WEP, WPA, etc.?

What you describe is the same problem I have with my XP laptop on my WPA2 network at home.  It can take 10 or more minutes to fully connect and authenticate, and to me it appears to be DHCP related.  I have no problems connecting to a WEP network.

I haven't spent the time to really try to track down the problem, so I don't know if it is with my laptop or the access point.  My wife's laptop doesn't seem to have a problem connecting and authenticating.

---

### Post by El Conquistador on 2008-07-29
Have you tried?:

dhclient [device name]

---

### Post by bshrum on 2008-07-29
I have tried dhclient and i still get no response.  I will try to post some code output tonight to see if we can narrow it down.  Thanks again for the responses.

---

### Post by eightmillion on 2008-07-29
bshrum,

You might give [WICD]("http://wicd.sourceforge.net/") a shot. I've had good luck with it when my card would fail to obtain an IP with the standard connection managers.

---

### Post by pedrogent on 2008-07-29
I agree that giving WICD a shot can't hurt.

---

### Post by JoneYee on 2008-07-29
I hate to ask this, but have you verified that the wireless router is not the problem?

I run a Linksys WRT350N and had problems with losing the SSID that were completely unrelated to Ubuntu, but made it look like there was a problem with Ubuntu's recognition of the wireless adapter.

The next time you run into problems, open terminal and give us the output of an iwconfig if you would.

---

### Post by bshrum on 2008-07-29
Yeah the router is fine.  I am posting on my powerbook via wireless at the moment.  I did however get an error on my powerbook about the ip i was using being in use when i turned my Unbutu system on.  Hmmmmmmmmm.

---

### Post by JoneYee on 2008-07-29
> **bshrum said:**
> Yeah the router is fine.  I am posting on my powerbook via wireless at the moment.  I did however get an error on my powerbook about the ip i was using being in use when i turned my Unbutu system on.  Hmmmmmmmmm.

May need to see about releasing/renewing ip addresses on your dhcp clients and check lease times from the router.

---

### Post by irshadcharm on 2008-07-29
how to configure my wireless in thinkpas x60? I'm experiencing problems with open wep key (linksys WRT54G router)....not able to connect even after entering the proper key...it checks for some time and asks for the key repeatedly.. help wud be appreciated...

---

### Post by bshrum on 2008-07-29
Dude seriously, create a separate thread for your problems, you will only confuse things here.

---

### Post by JoneYee on 2008-07-29
> **irshadcharm said:**
> how to configure my wireless in thinkpas x60? I'm experiencing problems with open wep key (linksys WRT54G router)....not able to connect even after entering the proper key...it checks for some time and asks for the key repeatedly.. help wud be appreciated...


Agreed this should be a new thread for your issue, however I would think straight off that you are set for 128 hexi instead of 64 bit ascii or visa versa.

---

