---
title: "Wi-Fi not being recognized"
date: 2008-05-28
forum: New to Ubuntu
---

### Post by OZFive on 2008-05-28
Okay here it is, 

I have a Sony Viao N325E laptop that I am running Ubuntu 8.10 on.

Wireless has worked fine up till yesterday.
I was messing around wiht the panel and i accidently removed the notification panel and whenI returned it it was fine but the WiFi bar meter was not back but everything ran fine.

This morning I turn it on and all is fine, the meter is back and WiFi is running normal.  

I turn it off to clean the screen and keyboard and when I turn it back on the meter is gone again and WiFi gone.

I have looked allover the forum to replace the meter and access the WiFi but all the sugestions are to no avail.

I even tried the Live cd to see if that would allow me to access it.  The Network Manager came up but did not show my wirelss or any WiFi network.

I tried a manual configuration of the network and I selected Wireless and unchecked the box "Enable Roamning" and lo and behold the WiFi netowkrs of the house and surrounding networks pop up in the drop down menu.  

So I know thew card is not acting up as the networks are showing on the manual configuration.  But eve though I try to log in to the WiFi Network manually I cannot access it still.

HELP!!!!

---

### Post by Fernanernie on 2008-05-28
Just use wicd and be done with the hassle.

---

### Post by Golem XIV on 2008-05-28
Maybe it's a stupid question, but when you wiped the laptop clean did you by any chance turn off the WiFi switch?

---

### Post by OZFive on 2008-05-28
What is wicd?

no I made sure the switch was on after cleaning.

---

### Post by Golem XIV on 2008-05-28
Wicd is a replacement for the default Ubuntu network manager.  The wicd site is [here]("http://wicd.sourceforge.net/"), take a look and see if you want to install it.

I have used it previously on Gutsy (7.10) and I liked it a lot, but I have less need for it now so I have not yet installed it.

Note that when you install wicd it will uninstall network-manager and network-manager-gnome, so if your wicd installation goes wrong or if wicd fails to work, you won't have a fallback.

I recommend that you first download these two packages from [here]("http://packages.ubuntu.com/hardy/net/") in case you have problems with wicd and you need to fall back to the old one.

Note:  I am assuming you are using Hardy (8.04).  Ubuntu 8.10 is not even alpha yet, so it's probably a typo, unless you're posting from the future :-)

---

### Post by OZFive on 2008-05-28
HA!   A Backyardigans Quote!

OKAY!  I got it fixed.  I plugged into  land line and went into the repositories via Syanptic and found that my Network Manager was out of date and needed to be upgraded.

I had what came with Hardy, I cannot remember the version number, but it needed to be upgraded to the new one.  I upgraded it and rebooted and sure enough there it was asking me for my WiFi key.

Thanks all for the help!

---

### Post by Golem XIV on 2008-05-28
> **OZFive said:**
> HA!   A Backyardigans Quote!

OKAY!  I got it fixed.  I plugged into  land line and went into the repositories via Syanptic and found that my Network Manager was out of date and needed to be upgraded.

I had what came with Hardy, I cannot remember the version number, but it needed to be upgraded to the new one.  I upgraded it and rebooted and sure enough there it was asking me for my WiFi key.

Thanks all for the help!

Yep, every evening my 4-year-old daughter likes to snuggle up with daddy to watch the Backyardigans :-)

Anyway, your network-manager packages are a lot newer than the ones I have (my Synaptic reports them to be 0.6.6, yours seem to be some kind of bleeding-edge SVN builds).  In any case, as long as they work it's fine.  Good luck!

---

