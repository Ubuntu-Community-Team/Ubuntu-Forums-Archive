---
title: "[SOLVED] joining/creating an ad hoc network"
date: 2008-07-16
forum: New to Ubuntu
---

### Post by gorgon on 2008-07-16
Hi!

Im quite fresh to the networking thing in ubuntu and would like to have an ad hoc network between an ubuntu and a osx machine.

Through NetworkManager I cant connect or create a network successfully, following [[COLOR="Orange"]this tutorial[/COLOR]]("https://help.ubuntu.com/community/WifiDocs/Adhoc") I was able to create a network but when I connected to it with the osx machine I could not ping either way.

Im quite lost when it comes to IP addresses, DHCP and all that stuff, could anyone point me in a direction?

Cheers!

---

### Post by halitech on 2008-07-16
are both machines setup with wireless cards or are you using a hub/switch/router or a cross over cable?

---

### Post by gorgon on 2008-07-16
hi, yea both are with wireless, no cable, no hub/router.

---

### Post by halitech on 2008-07-16
ok, the Mac side I'm rusty on so won't be able to help you much there. Have you assigned static IPs to both machines that are in the same network? (IE. 192.168.1.xx)

when you look in Network Manager on the Ubuntu comptuer, do you see a wireless network connection there?

I think on the Mac, it would be under System preferences - network and set it to static and assign the IP address you want.

---

### Post by gorgon on 2008-07-17
Ah, found the problem.

What the 'WifiDocs/Adhoc' tutorial that I mentioned in post 1 did not say is that it could be smart to define your netmask and broadcast ip.

I did this instead of the activation part in the document:
```
sudo ifconfig eth2 10.10.10.1 netmask 255.255.255.0 broadcast 10.10.10.255 up
```

and now I can have an ad-hoc from the ubuntu machine. nice.

thanks for your time halitech.

---

### Post by halitech on 2008-07-17
glad to hear you got it working :)

---

### Post by hogsmate on 2009-05-16
thanks guys this was really helpful :D

---

### Post by abdusamed on 2010-05-31
i wish it was that easy.. can u explain a bit more how did u do it? i don't want to create another thread--- spamming.. like okay..i created a new wirless network on ubuntu 10.04 now what?

---

### Post by abdusamed on 2010-05-31
okay.. i was a bit impatient.. but thankfully lucid fixed it.. i connected to the network and sharing right now.. but the problem was that the Vista created the network and i joined to it. After joining, it kept trying to connect and later it disconnected. But then i decided to change the setting of the network which i was connected to through the network manager .8. Going to the wireless tab and editing the connection setting. In the IP4, i set the option to shared dchp thingy and voila workin!! happy... but Vista machine wasn't able to connect to the network which i created with the password protection [WPA2 personal.. dunno if it was either 1 or 2 but it was WPA] Not only that, but when i create a WPA protected network on Vista machine, my ubuntu 10.04 doesn't seem to pick up the connection, like doesn't even try connecting to it. But if i create the protected network on ubuntu machine, the password passes on ubuntu but fails on Vista poping up a message saying that' the pass is has 10 character or 10=15 number with letter' junk.. what's the prob? right now i'm connected to a vista free to air network.. anyone can conncet..not only that.. i don't even know how many users are connected to my NETWORK... cuz if i knew..i could simply ban THEM!

---

### Post by Thierry51 on 2012-09-17
with the dhclient command?????

---

### Post by jimbosbees on 2012-09-18
let me know if this question fits here or where!!
changed att dsl to uverse router.  got xp pro, vista , and win 7 wireless changed over'
I have not the slightest idea what to do to convert 10.04 and 12.04 ubuntu, they were working wireless on dsl router,.. I hooked up by internet cable and 10.04 worked, did not try 12.04.
I am very much beginner so need step by step to succeed
thanks jimbosbees.
today 9/20 ubuntu 12.04 showed wireless connection available.  using the uverse router internal info i poked arount and got connection.  Am doing this post with 121.04.  retryed 10.04 wired, it surfed the internet, fire fox worked.  diconnected and tried wireless and no signal found, even after rebooting again.

Any help appreciated. i might even be able to follow command line if somebody can hold my hand. 
my time on this forum will vary from right away to days not psoting, depends on family and work demands.

---

