---
title: "Weird wireless problem"
date: 2008-08-08
forum: New to Ubuntu
---

### Post by shabs on 2008-08-08
Hi all,
I have a weird problem. I'm using hardy 8.04.1. Most times my wireless connection works fine but after a while it will just disconnect. The time varies greatly, sometimes it just keeps working while at other times it'll disconnect after a few minutes after I've connected. If I restart it at this point during the bootup I get this error:
" Starting bluetooth
xx.xxxxxx usb 5-3: Device Descriptor read /64 error 110 "
It flashes the above error a couple of times with the /64 reducing to /8.
When ever I get this error during bootup the wireless does not work. If I dont get this error while booting up the wireless works fine.
Also while surfing when it disconnects, I'm still able to see the wireless connection in the notification area. If I keep trying to connect it will finally disappear and there will be no wireless connections shown anymore. What do you think the problem is? I dont have blue tooth on my laptop. I've attaching the output of lspci -v.
Thanks.
I upgraded from gutsy to hardy (with a few problems ofcourse, gutsy was far better IMHO). In gutsy I had the same problem with the wireless internet but I never noticed the blue tooth message and the device descriptor errors.

---

### Post by Crafty Kisses on 2008-08-08
That's weird, it could be a possible driver issue. Since it's working with Linux already you probably don't need a Ndiswrapper.

Post these following outputs:
```
ifconfig
```

Also when the Internet drops, try this:
```
ping www.google.com
```
See if you get a reply.

---

### Post by shabs on 2008-08-10
Thanks for your reply codename,
I'm attaching the output of ifconfig. Sometimes the internet works fine the entire day and at times for a few mintues before it stops. And yesterday it worked fine except it was very very slow. I tried firefox, seamonkey, dillo and lynx, all very slow. Dillo was faster since its text based and seamonkey was marginally faster than firefox. Dont know if this is the same problem or something else.
I will try using another computer to find out what reply I get when I try to ping some address and come on here again.

---

### Post by Crafty Kisses on 2008-08-10
That's weird, do you have a encryption or a firewall on your wireless connection? 

Try a couple of different things here:

1. If you do have a encrypted connection, then turn off the firewall and see if that makes a difference, because I know my old router I had my firewall on and it made it slow for no reason, I took it off and it worked fine, I know it's weird.

2. If you are not on a encrypted connection, I'd suggest you encrypt it because It is quite possible someone is leeching of your connection and when you encrypt the connection they obviously can't connect to it anymore.

3. Sorry I didn't mention this before, post the following output of:
```
iwconfig
```

---

### Post by Mytth on 2008-08-10
I rarely get that problem, i think it is due to the wireless settings automatically changing for some reason,it  changes from ascii to 128 bit hex automatically, making it impossible to connect, i fix it by deleting the connection, and adding a wireless connection manually, and adding the coorect security settings.

---

### Post by epiphonygirl on 2008-08-10
I know that on my laptop when I leave my wireless hardware switch on when I shut my laptop off then restart with that switch still on it will not switch to wireless no matter how many times I flip the switch back and forth after start-up. If you have a wireless switch maybe leave it in the off position at start-up and turn it on once you reach the desktop?

---

### Post by shabs on 2008-08-13
I've attached the output of iwconfig.

@codename. The connection is not encrypted and anyone within range can connect to it. Yes I know I know I should do something about it :D but its my  uncles connection and I'd have to ask first anyway. Also there are two laptops in the house. The other one works fine and fast, so do the other wired connections. So I doubt its because of someone leeching. However this problem rises after I'm able to connect :) At times it wont even let me connect. After it connects it will disconnect every few minutes and reconnect by itself sometimes or I have to do it manually. And if it doesnt connect I let it sit for a while and if I try again it connects. and the cycle continues. I doubt if theres a firewall activated on the router (I dont know that much about routers tho). If there was one wouldnt it affect the laptop with windows on it too? The laptop with windows works fine and so did mine until I used windows.
Also to answer a question you asked in the post previous to this: When I ping [www.anywebsite.com](www.anywebsite.com) while its not working I get a reply that says 'unknown host'

@mytth. There are no security settings so do I still need to manually add the connection?

@epiphonygirl. The wireless on my laptop with ubuntu works irrespective of whether the wireless switch is in the on or off position.

What do you guys think?

---

### Post by okey666 on 2008-08-13
Try using a different wireless manger. I had the same problem using madwifi atheros drivers. Try using wicd (Google it, it needs its own repro). I had trouble with that and eventually settled with the very basic (but still sufficient) rutilt (which is in the repros).

---

### Post by shabs on 2008-08-13
I suppose I'm using the default 'Network Manager'. I will give wicd a try to see if it fixes the problem. Do I uninstall network manager first?

---

### Post by okey666 on 2008-08-13
> **shabs said:**
> I suppose I'm using the default 'Network Manager'. I will give wicd a try to see if it fixes the problem. Do I uninstall network manager first?

Wicd will get rid of the network manger. However remember you will be left with no connection at all so download the network manager packages first so you can replace them if need be.

---

### Post by shabs on 2008-08-13
Well I didnt read your message before I went ahead and installed wicd. The speed of the wireless is still the same, very slow. So I tried rutilt. It didnt really work so now I'm with wicd. The wired connection is fast just like when I was using network manager. Before I upgraded, when ever the wireless worked it was lighting fast with gutsy. But because at times it would work and at times it wouldnt I decided to upgrade to hardy.

---

### Post by shabs on 2008-08-13
*ignore this, replied again by accident :D*

---

