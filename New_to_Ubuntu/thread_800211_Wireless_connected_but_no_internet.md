---
title: "Wireless connected but no internet"
date: 2008-05-19
forum: New to Ubuntu
---

### Post by alexnublet85 on 2008-05-19
Hi all,

So everything was going good, I installed my Belkin F5D6001 using ndiswrapper and driver net8180.inf and blacklisted stuff and everything seemed fine.

Then I decided to get Wine so I could try and run WoW.

When trying to sudo apt-get update, it failed in ways I can't show you now because I can't get back online. Something about broken packages. So I went to Winehq to download it and again said I had broken packages. So I tried to get updates still and look up removing wine.

Somewhere, somehow, my internet suddenly stopped working. When I click on the network I get an error box come up saying:

"Error connecting to wireless network
The requested wireless network requires security capabilities unsupported by your hardware."

And yet it still seems to get a signal but I can't get on any websites. I just don't understand what has happened and gone wrong, I don't know if it has anything to do with Wine and the updates but that was the last thing I was trying to do.

I don't understand how it is suddenly unsupported by my hardware when I was just using it a minute ago?

I really don't want to reformat, this will be the sixth time and everytime ndiswrapper takes me 2 days to fix.

It might just be me but it seems similar to my problem in XP that I can pick up the signal but something is blocking me from accessing it?

Please help :(

Alex

---

### Post by steve allen on 2008-05-19
> **alexnublet85 said:**
> Hi all,

So everything was going good, I installed my Belkin F5D6001 using ndiswrapper and driver net8180.inf and blacklisted stuff and everything seemed fine.

Then I decided to get Wine so I could try and run WoW.

When trying to sudo apt-get update, it failed in ways I can't show you now because I can't get back online. Something about broken packages. So I went to Winehq to download it and again said I had broken packages. So I tried to get updates still and look up removing wine.

Somewhere, somehow, my internet suddenly stopped working. When I click on the network I get an error box come up saying:

"Error connecting to wireless network
The requested wireless network requires security capabilities unsupported by your hardware."

And yet it still seems to get a signal but I can't get on any websites. I just don't understand what has happened and gone wrong, I don't know if it has anything to do with Wine and the updates but that was the last thing I was trying to do.

I don't understand how it is suddenly unsupported by my hardware when I was just using it a minute ago?

I really don't want to reformat, this will be the sixth time and everytime ndiswrapper takes me 2 days to fix.

It might just be me but it seems similar to my problem in XP that I can pick up the signal but something is blocking me from accessing it?

Please help :(

Alex

Have you tried going to System/Administration/Synaptic Package Manager click on broken and it will deal with broken packages

regards
steve

---

### Post by mapes12 on 2008-05-19
I got one of these and it works a treat:

Comtrend RT2500 54 Mbps Wireless PCMCIA card

A tenner from these guys:

[http://www.linuxemporium.co.uk/products/wireless/](http://www.linuxemporium.co.uk/products/wireless/)

Before, I had a Linksys adapter that needed an XP driver via ndiswrapper to work. It worked OK to begin with but then the configuration kept cracking up.............drove me nuts.

---

### Post by EnergySamus on 2008-05-19
Hi!

Is your router set to WPA or WPA-2? Check to see if that helps!

EnergySamus

---

### Post by alexnublet85 on 2008-05-19
I really don't want to have to buy anything new, for one everything on my computer is pretty old so compatibility is a bit of a problem, and two I don't think I should have to buy anything when it does work and was working?

I tried the broken packages thing and I got a long list of errors that I got before starting with:

W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dlists/hardy/Release.gpg](http://gb.archive.ubuntu.com/ubuntu/dlists/hardy/Release.gpg) Could not resolve 'gb.archive.ubuntu.com'

and more including [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) etc

all gpg stuff.

I guess this is because I am not online, but even when I was this is what happened.

Would broken packages be screwing with my internet?

---

### Post by alexnublet85 on 2008-05-19
regarding WPA or WPA2 on the router I don't know and can't check coz it's in my dam flatmates room and he's gone to bed

I thought I would try and put the key as WPA2 and see if that worked but now when I try and 'Connect to other wireless networks' I get this error:

The NetworkManager Applet could not find some required resources (the glade file was not found).

Maybe it's Network Manager that's screwed?

---

### Post by steve allen on 2008-05-19
I know that my computer would not do much when I had 3 broken packages and all was solved after using synaptic to fix.

I'm affraid I can't be a lot more help ubuntu/linux newbie

---

### Post by alexnublet85 on 2008-05-19
*accidentally double posted*

---

